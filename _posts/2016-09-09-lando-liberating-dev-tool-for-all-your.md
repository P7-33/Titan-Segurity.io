---
title: 'Lando: A Liberating Dev Tool for All Your Projects'
date: 2019-10-20T02:17:00+01:00
draft: false
---

![](https://raw.githubusercontent.com/lando/lando/master/docs/.vuepress/public/images/hero-pink.png "A Local Dev Tool For Every Project | Lando")  

### Initialize a codebase for usage with Lando

This will create a starter Lando config file that you can then slowly augment with further dependencies as needed. You can initialize from code in a local folder or pull in code from a remote archive, git repo, GitHub or [Pantheon](https://pantheon.io)!

Here are a few examples...

```
# Interactively initialize your code lando init 
```

```
# Set up a mean recipe that runs on a particular port with a particular command lando init --source cwd \ --recipe mean \ --option port=3000 \ --option command="yarn watch" \ --name meanest-app-youve-ever-seen 
```

```
# Interactively clone a site from Pantheon lando init --source pantheon 
```

```
# Spin up a new Drupal 7 site lando init \ --source remote \ --remote-url https://ftp.drupal.org/files/projects/drupal-7.59.tar.gz \ --remote-options="--strip-components 1" \ --recipe drupal7 --webroot . \ --name hello-drupal7 
```

### Optionally customize for MOAR POWER

While our recipe defaults are plenty good for most use cases Lando let's you customize further. This means you can configure our [recipes](https://docs.lando.dev/config/recipes.html#config), add [additional services](https://docs.lando.dev/config/services.html#services), [proxy routes](https://docs.lando.dev/config/proxy.html#proxy), [tooling commands](https://docs.lando.dev/config/tooling.html#tooling), [build steps](https://docs.lando.dev/config/services.html#build-steps), [runtime automation](https://docs.lando.dev/config/events.html#events), and [Docker Compose overrides](https://docs.lando.dev/config/services.html#overrides) or do nothing at all!

Here is a progressively complexifying WordPress example...

#### [#](https://lando.dev#default-wordpress-recipe-landofile-config) Default WordPress recipe Landofile config

```
name: my-app recipe: wordpress 
```

#### [#](https://lando.dev#adding-some-basic-recipe-config) Adding some basic recipe config

```
name: my-app recipe: wordpress config: database: postgres php: '7.3' xdebug: true 
```

```
name: my-app recipe: wordpress config: database: postgres php: '7.3' xdebug: true config: php: my-custom-php.ini proxy: pma: - database-my-app.lndo.site services: index: type: solr node: type: node:10 globals: gulp: latest pma: type: phpmyadmin hosts: - database tooling: yarn: service: node node: service: node 
```

#### [#](https://lando.dev#adding-php-extensions-build-steps-automation-docker-overrides) Adding php extensions, build steps, automation, docker overrides

```
name: my-app recipe: wordpress config: database: postgres php: '7.3' xdebug: true config: php: my-custom-php.ini events: post-db-import: - appserver: wp search-replace proxy: pma: - database-my-app.lndo.site services: appserver: build_as_root: - apt update -y && apt-get install vim -y - /helpers/my-script-to-install-php-extension.sh memcached build: - composer install overrides: environment: APP_LEVEL: dev TAYLOR: swift index: type: solr node: type: node:10 globals: gulp: latest build: - yarn frontend: type: node:10 command: yarn start build: - yarn pma: type: phpmyadmin hosts: - database tooling: yarn: service: node node: service: node gulp: service: node test: cmd: - appserver: composer test - frontend: yarn test deploy: service: appserver cmd: /path/to/script.sh 
```

### Try out some tooling commands

Lando isn't only about containerized services to run your application it also containerizes common dev tools like `node`, `composer`, `drush`, `artisan` and `python`. Try running `lando` after you start a project to see the tools available to your app, or [add additional tooling](https://lando.dev).

Here are some commands for our complex WordPress config above.

```
# See what tools are available in your app lando 
```

```
# Run wp-cli commands lando wp # Drop into a postgres shell lando psql # Import a database lando db-import dump.sql # Run composer and yarn tests lando test # Install more node packages lando yarn add bootstrap # Start up gulp watch lando gulp watch 
```

Once you are feeling good about your Landofile, commit it to your repository so other developers can easily get setup.

#### [#](https://lando.dev#project-lead-commits) Project lead commits

```
# Commit and deploy git add .lando.yml git commit -m "Supercharge my dev" git push 
```

#### [#](https://lando.dev#other-developers-get) Other developers get

```
# Get the project git clone my-project cd my-project # Start lando and get all the things you need lando start 
```

  
  
from Hacker News https://lando.dev