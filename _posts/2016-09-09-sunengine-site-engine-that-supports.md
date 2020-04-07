---
title: 'SunEngine – Site engine that supports forums, articles and blogs'
date: 2019-12-28T01:03:00+01:00
draft: false
---

[](https://github.com/sunengine/SunEngine#sunengine)SunEngine
=============================================================

Site engine with support of blog, forum and articles functionality.

[![SunEngine Logo](https://github.com/Dmitrij-Polyanin/SunEngine/raw/master/SunEngine.svg?sanitize=true)](https://github.com/Dmitrij-Polyanin/SunEngine/blob/master/SunEngine.svg)

[![](https://camo.githubusercontent.com/da8d69a188ff6d962f972478ecdb00b8b00711a6/68747470733a2f2f696d672e736869656c64732e696f2f7374617469632f76313f6c6162656c3d56657273696f6e266d6573736167653d322e302e302d72632e3926636f6c6f723d677265656e)](https://camo.githubusercontent.com/da8d69a188ff6d962f972478ecdb00b8b00711a6/68747470733a2f2f696d672e736869656c64732e696f2f7374617469632f76313f6c6162656c3d56657273696f6e266d6573736167653d322e302e302d72632e3926636f6c6f723d677265656e) [![](https://camo.githubusercontent.com/5a175662a7e6524c848ae8d7faa3c7ec373475b5/68747470733a2f2f696d672e736869656c64732e696f2f7374617469632f76313f6c6162656c3d44656d6f266d6573736167653d64656d6f2e73756e656e67696e652e7369746526636f6c6f723d696e666f726d6174696f6e616c)](https://demo.sunengine.site) [![](https://camo.githubusercontent.com/efcd02d736d4a793dd990f4c109a464535313407/68747470733a2f2f696d672e736869656c64732e696f2f7374617469632f76313f6c6162656c3d54656c656772616d266d6573736167653d4053756e456e67696e6526636f6c6f723d696e666f726d6174696f6e616c)](https://t.me/SunEngine) [![](https://camo.githubusercontent.com/45147991b957eda9b9d5d3425bf102233e3a83d7/68747470733a2f2f696d672e736869656c64732e696f2f7374617469632f76313f6c6162656c3d5275737369616e266d6573736167653d726561646d6526636f6c6f723d696e666f726d6174696f6e616c)](https://github.com/sunengine/SunEngine/blob/master/README.RU.md)

### [](https://github.com/sunengine/SunEngine#about-project)About project

#### [](https://github.com/sunengine/SunEngine#core-modules)Core modules

#### [](https://github.com/sunengine/SunEngine#friendly-interface)Friendly interface

*   Single-page application with a beautiful interface.
*   Works on personal computers, tablets and mobile phones.

#### [](https://github.com/sunengine/SunEngine#made-with-love-)Made with love ❤

*   Beautiful code that we constantly improve.
*   We are open to new ideas for improving code and architecture.

#### [](https://github.com/sunengine/SunEngine#key-technologies)Key technologies

The project uses modern and beautiful technologies.

*   Asp.Net Core 3.0
*   Linq2db — database framework.
*   FluentMigrator — database migrations.
*   VueJs — SPA-based client side.
*   Quasar Framework — vue components.
*   Database — any compatible with Linq2db and FluentMigrator.

#### [](https://github.com/sunengine/SunEngine#performance)Performance

*   Fast data access based on linq2db.
*   Single-page application loads only necessary data, without extra requests.
*   Efficient caching.

#### [](https://github.com/sunengine/SunEngine#flexible-configuration-of-user-role-rights)Flexible configuration of user role rights

*   Opportunity for each section — site's category — set different access rights for different groups of users.

#### [](https://github.com/sunengine/SunEngine#admin-panel)Admin panel

*   Edit site sections — categories.
*   Edit site menu.
*   Edit user roles.
*   Customize caching.

#### [](https://github.com/sunengine/SunEngine#deployment)Deployment

*   Works on Windows, Linux and macOS.
*   Compatible with most relational databases.

### [](https://github.com/sunengine/SunEngine#launch-prerequisites)Launch prerequisites

SunEngine can be launched on Windows, Linux and macOS.

To run the project you need to install:

### [](https://github.com/sunengine/SunEngine#launch-for-development)Launch for development

#### [](https://github.com/sunengine/SunEngine#launch-from-console)Launch from console

1.  Download the project code from the official repository [https://github.com/sunengine/SunEngine](https://github.com/sunengine/SunEngine) (if not done)
2.  Rename files and folders with the suffix `-template`, and remove this suffix. (if not done)
3.  Go to folder `SunEngine/SunEngine.Cli`.
4.  Create a database `SunEngine` in the selected DBMS. (if not done)
5.  Register the provider name and connection string in the file `SunEngine/SunEngine.Cli/Config/DataBaseConnection.json`.
6.  Fill the database with initial data `dotnet run migrate init seed` (if not done).
7.  Run server `dotnet run server`.
8.  Go to folder `SunEngine/Client`.
9.  Install npm modules `npm install` (if not done yet).
10.  Run client `quasar dev` — browser will be opened.

### [](https://github.com/sunengine/SunEngine#contacts)Contacts

  
  
from Hacker News https://github.com/sunengine/SunEngine