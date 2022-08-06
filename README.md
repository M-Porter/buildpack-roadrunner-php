# buildpack-roadrunner-php

A Heroku buildpack for roadrunner.

## Usage

### Adding the buildpack

```
heroku buildpacks:add https://github.com/M-Porter/buildpack-roadrunner-php
```

#### Specifying the roadrunner version

You can specify which roadrunner version to use by setting the `RR_VERSION` environment variable.

### Procfile

```yaml
web: ./rr -o http.address=0.0.0.0:${PORT} serve
```

### `.rr.yaml`

The following config assumes you have a [worker file](https://roadrunner.dev/docs/php-worker/2.x/en) at your project root named `worker.php`.

```yaml
# configuration version: https://roadrunner.dev/docs/beep-beep-config/2.x/en
version: '2.7'

rpc:
  listen: tcp://127.0.0.1:6001

server:
  command: "php worker.php"

logs:
  mode: production
  level: info
  output: stdout
  encoding: json
```
