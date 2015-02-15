Foreman concurrency plugin for dokku-alt
------------------------------------

Source: https://github.com/clearbit/dokku-alt-foreman


Installation
------------
```
cd /var/lib/dokku/plugins
git clone https://github.com/clearbit/dokku-alt-foreman foreman
dokku plugins-install
```

Commands
--------
```
$ dokku help
     foreman:install <app>               Installs the default foreman concurrency controls
     foreman:set     <app> <concurrency> Configures the concurrency
```

Simple usage
------------

To set the default concurrency controls which will start only the web process:

```
$ dokku foreman:install my_app
```

This is equivalent to running `foreman -c web=1` when the container starts.

To adjust the concurrency:

```
$ dokku foreman:set web=0,sidekiq=1
```

Note: `foreman:install` is not required before using `foreman:set`. If you are
planning to use non-default concurrency it's recommended to use `foreman:set`
with your desired values without calling `foreman:install` first. This
avoids restarting your app twice (and possibly firing up processes you didn't
wish to be running).
