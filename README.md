dokku-link
==========

Basic docker link plugin for dokku (https://github.com/progrium/dokku)

For a more useful dokku plugin, which will also handle persistent storage, check out dokku-docker-options (https://github.com/dyson/dokku-docker-options).

Requirements
------------

Development version of dokku at or after https://github.com/progrium/dokku/commit/c77cbf1d3ae07f0eafb85082ed7edcae9e836147.

Installation
------------

````
cd /var/lib/dokku/plugins
sudo git clone https://github.com/rlaneve/dokku-link.git link
````

Usage
-----

In your applications folder (/home/dokku/app_name) create a file called LINK.

Inside this file list the secondary container to which you want docker to establish a link for your app. For example:

````
pgsql:db
````

The above example will result in the following arguments being passed to docker during deploy and docker run:

````
-link pgsql:db
````

More information on docker links can be found here: http://docs.docker.io/en/latest/use/working_with_links_names/

Commands
--------
```
$ dokku help
    link <app>                                      display links for an app
    link:create <app> NAME [ALIAS]                  create a link for an app
    link:delete <app> NAME [ALIAS]                  delete a link for an app
```

After creating or deleting a link you must redeploy the app.

License
-------

MIT.
