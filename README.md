# duplicity
Duplicity for Docker

This is a very basic Docker image with Duplicity and Dropbox & OAuth2 support.
You can simply create your app at dropbox.com/developers, generate auth token, create folder "backups" inside the "app folder" and run image:
```
docker run --rm -h duplicity -v /stuff/to/backup:/mount/in/container -v duplicity:/root -e DPBX_ACCESS_TOKEN="" -e PASSPHRASE="" duplicity <command>
```
<command> example:
```
full /mount/in/container dpbx:///backups
```
This container is just a wrapper for duplicity so any duplicity command is supported.
With the example <command> metadata is stored in "duplicity" Docker volume and backup sent to "backups" Dropbox folder.
Do not forget to set "-h duplicity" parameter, otherwise pass --allow-source-mismatch argument on the next run.