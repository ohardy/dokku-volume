# Volume (persistent storage) plugin for Dokku

Project: https://github.com/progrium/dokku

## Installation

```
cd /var/lib/dokku/plugins
git clone https://github.com/ohardy/dokku-volume volume
dokku plugins-install
```


## Commands
```
$ dokku help
    volume:env         <app>                                         Get generated environment variables for <app>
    volume:add         <app> <container_path>                        Mount a folder in <app> at <container_path>
    volume:remove      <app> <container_path>                        Remove folder in <app> at <container_path>
    volume:dump        <app> <container_path> > filename.tar.gz      Dump volume data to filename.tar.gz
    volume:retore      <app> <container_path> < filename.tar.gz      Restore volume data from filename.tar.gz
    volume:list        <app>                                         Give list of volumes for <app>
    volume:update                                                    Update this plugin
    volume:migrate                                                   Migrate
```

## Updating this plugin
Dokku doesn't handle plugin update. I made a pull request to dokku for that (https://github.com/progrium/dokku/pull/669)

So, each time you update this plugin with `git pull`, you need to call:
```
$ dokku volume:migrate
```

## Info
This plugin mount container_path to a generated folder in /home/dokku/.o_volume :

## Usage

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
