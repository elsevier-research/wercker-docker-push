# wercker-docker-push

This wercker step just push your package to a [Docker](https://docs.docker.com/reference/commandline/cli/#push) registry.

This step must be used with a wercker box built with [Docker Support](http://devcenter.wercker.com/articles/docker)


## Versions

| Release date | Step version | Docker version |
| -------------| -------------| ---------------|
| 2014-12-01   | 1.0.2        | 1.3.1          |
| 2014-11-28   | 1.0.1        | 1.3.1          |


## Options

* `image` (required) Image to push to the registry
* `registry` (optional) Docker registry server, if no server is specified "https://index.docker.io/v1/" is the default.
* `username` (required) Username needed to login to the Docker registry
* `password` (required) Password needed to login to the Docker registry
* `email` (required) Email needed to login to the Docker registry

## Example


The following example push a [previously built](https://github.com/nhuray/wercker-docker-build) docker image to a
private [tutum.co](https://www.tutum.co/) registry :

```
deploy:
  steps:
    ...
    - nhuray/docker-push:
        image: tutum.co/nhuray/myimage:${WERCKER_GIT_COMMIT:0:7}
        registry: tutum.co
        email: nicolas.huray@gmail.com
        password: *****
        username: nhuray
```
