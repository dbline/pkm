---
id: ksxsc8hpmm29hkqi4rj8954
title: smithworks POS import
desc: ''
updated: 1647287059279
created: 1646674955779
---

```bash ^brw2xldvcby1
tsj smith<tab>
infile=$(ls -t $ftp_path/*-INVENTORY-FULL.CSV|head -1)
cp Smithworks_cp Smithworks_168_Stock_03_06_2022.csv ~/dbl
sed -i "s/RawImageData/itImage/g" Smithworks_168_Stock_03_06_2022.csv
manage.py pointofsale_import --edge --filename=Smithworks_168_Stock_03_06_2022.csv --image-dir=/srv/volumes/ftp-data/smithworksjewelers-ftp/images/ -v2 | tee smithworks.log
```
### import_edge_catchup script
```bash
BASE_DIR=/home/typethink/.virtualenvs/pine-celery
LOG_DIR=$BASE_DIR/log
LOG_PREFIX="import_edge"
LOG_FILE=$LOG_DIR/${LOG_PREFIX}-${TSJ_SITE}-$(date +%Y%m%d)-full.log
ftp_root="${FTP_ROOT:-/srv/volumes/ftp-data}"
if [ -z "$VIRTUAL_ENV" ] ; then
  . $BASE_DIR/bin/activate
  . $BASE_DIR/bin/postactivate
fi

cd $BASE_DIR
# FTP username and path
ftp_username=$(manage.py get_pref tsj_pointofsale ftp_username 2>/dev/null)
ftp_path=$(realpath "$ftp_root/$ftp_username")

checked_import() {
  echo importing edge file $1
  manage.py pointofsale_import --edge --filename=$1 -v2
  echo imported edge file $1
}

# Find the newest full inventory file in each FTP directory
infile=$(ls -t $ftp_path/*-INVENTORY-FULL.CSV|head -1)
header_length=$(head -1 $infile|wc -c)
if [[ $header_length -lt 50 ]] ; then
  echo $infile is too short.
  echo Exiting
  exit 1
else
  header_length=$((1 + $header_length))
fi

# Creation time in unix epoc time
sinfile=$(stat -c %Z "$infile")

# Give the time information
echo infile $(realpath --relative-to=$ftp_root $infile) $(stat -c %y "$infile") | tee -a $LOG_FILE

# Find the partials that are newer than the fulls in each FTP directory.
# Also larger than 1918, which is the headers size.
partial_files=$(find $ftp_path -name "*-INVENTORY.CSV" -newer $infile -size +${header_length}c)

[ -z "$partial_files" ] && echo no newer partials in primary FTP | tee -a $LOG_FILE
if [ -z "$partial_files" ] ; then
  echo DO NOT type Y if you were expecting partials. | tee -a $LOG_FILE
  sorted_partial_files=
else
    # Combine and sort for time.
  sorted_partial_files=$(ls -tr $partial_files)

  # Display an easier to read list of partials.
  realpath --relative-to=$ftp_root $sorted_partial_files | tee -a $LOG_FILE
fi

do_dangerious_stuff() {
  # This will be True for partial and False for full.
  _partial=$(manage.py get_pref tsj_pointofsale partial_import 2>/dev/null)
  if [ "$_partial" = "True" ] ; then
    echo set_full
    manage.py set_import_pref partial_import &>/dev/null
  fi

  TMP_DIR=$(mktemp --directory)

  # Import the fulls.
  checked_import $infile

  echo set_partial
  manage.py set_import_pref partial_import -s &>/dev/null

  # Import the partials in order.
  if [ ! -z "$sorted_partial_files" ] ; then
    for f in $sorted_partial_files ; do
      checked_import $f
    done
  fi

  rmdir $TMP_DIR

  # If we were on fulls before, set back to full.
  if [ ! "$_partial" = "True" ] ; then
    echo set_full
    manage.py set_import_pref partial_import &>/dev/null
  fi

  # NOTE: these are work arounds for
  manage.py bust_catalog_cache --redis-itemprice --filtersets --redis-itemimg
  echo busted cache for item prices, filtersets and item images
}

# Confirm run.
echo We are going to import the above full files as fulls, then the above partials as partials.
echo This will take awhile.
echo $LOG_FILE
read -p "Are you sure? " -n 1 -r
echo    # (optional) move to a new line
if [[ $REPLY =~ ^[Yy]$ ]]
then
  do_dangerious_stuff |& tee -a $LOG_FILE
  echo $LOG_FILE
fi

```