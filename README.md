## Installing Prerequisites

```shell
brew install caskroom/cask/brew-cask
brew cask install boot2docker
brew install direnv fig
```

## Readying Docker

```shell
boot2docker init
boot2docker upgrade
boot2docker up
docker version
docker ps
```

## Boot A Variant

```shell
fig up -f fig/$name.yml
```

## TODO

* Vagrantfile
