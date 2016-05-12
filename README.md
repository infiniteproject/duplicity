# duplicity
Duplicity for Docker

Dropbox & OAuth2 is supported; create app at dropbox.com/developers, generate auth token, create folder "backups" inside the "app folder" and run image as:
```
docker run --rm -h duplicity -v /stuff/to/backup:/source -v duplicity:/root -e DPBX_ACCESS_TOKEN="" -e PASSPHRASE="" duplicity full /source dpbx:///backups
```
Metadata is stored in "duplicity" Docker volume and backup sent to "backups" Dropbox folder. Do not forget to set "-h duplicity" parameter, otherwise pass --allow-source-mismatch argument on the next run. Can be run via cron (on the host!) 

/etc/cron.d/duplicity:
```
0 0 * * * root /usr/local/sbin/backup.sh >/dev/null 2>&1
```
