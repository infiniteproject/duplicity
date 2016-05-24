[![Build Status](https://travis-ci.org/infiniteproject/duplicity.svg?branch=master)](https://travis-ci.org/infiniteproject/duplicity)
# duplicity
Duplicity for Docker

This is a very basic Docker image with Duplicity and Dropbox & OAuth2 support (from Ubuntu PPA).
You can simply create your app at dropbox.com/developers, generate auth token, create folder "backups" inside the "app folder" and run image:
```
docker run --rm -h duply -v /files:/source -v duply:/root \
  -e DPBX_ACCESS_TOKEN="" \
  -e PASSPHRASE="" \
  duplicity full /source dpbx:///backups
```

This container is just a wrapper for duplicity so any duplicity command is supported.
With the example command metadata is stored in "duply" Docker volume (and then reused) and backup sent to "backups" Dropbox folder.
Do not forget to set "-h duply" parameter, otherwise pass --allow-source-mismatch argument on the next run.
