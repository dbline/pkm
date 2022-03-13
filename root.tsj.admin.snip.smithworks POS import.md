---
id: ksxsc8hpmm29hkqi4rj8954
title: smithworks POS import
desc: ''
updated: 1646685828144
created: 1646674955779
---

```bash ^brw2xldvcby1
tsj smith<tab>
cp Smithworks_cp Smithworks_168_Stock_03_06_2022.csv ~/dbl
sed -i "s/RawImageData/itImage/g" Smithworks_168_Stock_03_06_2022.csv
manage.py pointofsale_import --edge --filename=Smithworks_168_Stock_03_06_2022.csv --image-dir=/srv/volumes/ftp-data/smithworksjewelers-ftp/images/ -v2 | tee smithworks.log

``` 
