## Installing Prerequisites

```shell
brew update
brew install caskroom/cask/brew-cask
brew cask install boot2docker
brew install fig
```

Optionally, you can use `direnv` to automatically set some environment variables, sourced from `.envrc`:
```shell
brew install direnv
direnv allow .
```

## Readying Docker

```shell
boot2docker init
boot2docker upgrade
boot2docker up
docker version
docker ps
```

## Boot The App

From the root of the repository:

```shell
fig pull && fig build
fig up -d
```

## Inspection
### Consul Registered Services

```shell
curl http://`boot2docker ip 2>/dev/null`:8500/v1/catalog/services
```

### Visit LB In Default Browser

```shell
open "http://`boot2docker ip 2>/dev/null`/"
```

## Adding/Removing Backend Containers

```shell
fig scale app=4
fig scale app=1
```

## Gotchas
* The auto-detected advertise IP for Consul-in-Docker on Boot2docker does not appear to be routable from the Nginx container. Use the following to look up the IP to set for `-advertise`:

```shell
boot2docker ssh ifconfig eth0 | grep 'inet addr'
```
