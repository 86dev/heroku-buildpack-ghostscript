# Heroku Buildpack for Ghostscript

## Currently installs Ghostscript 10.01.2 on Heroku.

#### Customize

If needed, you can set environment variables to customize package url and binary path:

- GHOSTSCRIPT_PACKAGE="https://github.com/ArtifexSoftware/ghostpdl-downloads/releases/download/gs10012/gs_10.01.2_amd64_snap.tgz"
- GHOSTSCRIPT_BINARY="gs_10.01.2_amd64_snap/gs_10.01.2_amd64.snap"

You can omit GHOSTSCRIPT_BINARY if the naming convention still applies. Currently (2023-07-12), it is `$archive_name_without_extension/${archive_name_without_extension/_snap/.snap}`.

#### Install

```shell
$ cd /path/to/your-app
$ heroku buildpacks:add https://github.com/86dev/heroku-buildpack-ghostscript.git

# Push changes to deploy
$ git push heroku master

# This version of ghostscript will end up deployed at /app/vendor/gs/bin/gs
# So you may want to set an environment variable to let your app know where it is. e.g.
$ heroku config:set GS_PATH=/app/vendor/gs/bin/gs
```

#### Thanks

Thanks to [Wilfirson](https://github.com/Wilfison/heroku-buildpack-ghostscript) and all others before him for the script
