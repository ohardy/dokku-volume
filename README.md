# Volume (persistent storage) plugin for Dokku [![Build Status](https://img.shields.io/travis/ohardy/dokku-volume.svg?branch=master "Build Status")](https://travis-ci.org/ohardy/dokku-volume)

Project: https://github.com/progrium/dokku

## requirements

- dokku 0.4.0+
- docker 1.8.x

## installation

```shell
# on 0.3.x
cd /var/lib/dokku/plugins
git clone https://github.com/ohardy/dokku-volume.git volume
dokku plugins-install

# on 0.4.x
dokku plugin:install https://github.com/ohardy/dokku-volume.git volume
```

## commands
```
$ dokku help
    volume:env <app>                                          Get generated environment variables for <app>
    volume:add <app> <container_path>                         Mount a folder in <app> at <container_path>
    volume:remove <app> <container_path>                      Remove folder in <app> at <container_path>
    volume:dump <app> <container_path> > filename.tar.gz      Dump volume data to filename.tar.gz
    volume:restore <app> <container_path> < filename.tar.gz   Restore volume data from filename.tar.gz
    volume:list <app>                                         Give list of volumes for <app>
    volume:update                                             Update this plugin
    volume:migrate                                            Migrate
```

## info
This plugin mount container_path to a generated folder in /home/dokku/.o_volume :

## usage

### Add volume:
```
$ dokku volume:add foo /path/in/container                 # Server side
..or..
$ ssh dokku@server volume:add foo /path/in/container      # Client side

```

### Remove volume:
```
$ dokku volume:remove foo /path/in/container              # Server side
..or..
$ ssh dokku@server volume:remove foo /path/in/container   # Client side

```

### Dump volume to tar.gz archive:
```
$ dokku volume:dump foo /path/in/container > foo.tar.gz            # Server side
..or..
$ ssh dokku@server volume:dump foo /path/in/container > foo.tar.gz # Client side
```

### Restore volume from archive:
```
$ dokku volume:restore foo /path/in/container < foo.tar.gz            # Server side
..or..
$ ssh dokku@server volume:restore foo /path/in/container < foo.tar.gz # Client side
```
