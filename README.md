# exim-relay

Base from work of https://github.com/selim13/docker-exim-relay

This is a base Exim docker image configured to act as a relay with some basic
`main`, `acl` and `retry` defaults.

No `routers`, `transports` or `authenticators` are configured, so by default it will
fail delivering all mail.

You can use it as a base for your docker images. Put your configuration
either to `/etc/exim/exim.conf` or to the following included files:
* `/etc/exim/conf.d/main.conf`
* `/etc/exim/conf.d/acl.conf`
* `/etc/exim/conf.d/routers.conf`
* `/etc/exim/conf.d/transports.conf`
* `/etc/exim/conf.d/retry.conf`
* `/etc/exim/conf.d/rewrite.conf`
* `/etc/exim/conf.d/authenticators.conf`
* `/etc/exim/conf.d/local_scan.conf`

## Environment variables

### EXIM_RELAY_FROM_HOSTS
Sets `relay_from_hosts` host list which is used in acl checks.

Default value: `10.0.0.0/8 : 172.16.0.0/12 : 192.168.0.0/16`

#### Docker compose usage
```
version: '2'

services:

mail:
    build: ./docker/docker-exim-relay
    ports:
        - "25:25"
    environment:
        - EXIM_GMAIL_LOGIN=******@gmail.com
        - EXIM_GMAIL_PASSWORD=**********
```
