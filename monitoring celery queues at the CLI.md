---
id: 63MgCuvUTjwv4Qnws5xRq
title: Monitoring the celery queues at the CLI
desc: ''
updated: 1642616943363
created: 1642610959599
---

tsj23

"ls ~/bin/*queue*"

(pine-celery) typethink@tsj23:ramseys_19 /home/typethink/sites/ramseys_19/templates/tsj_catalog_local$ ls ~/bin/*queue*
/home/typethink/bin/list-celery-queues   /home/typethink/bin/queue-check-nagios          /home/typethink/bin/watch-queues
/home/typethink/bin/list_queues          /home/typethink/bin/queue-check-nagios~
/home/typethink/bin/maybe-restart-queue  /home/typethink/bin/queue-check-nagios-no-null


We were way behind in the default celery-default queue.  There were 3 workers and it got increased to 7 at the moment.
