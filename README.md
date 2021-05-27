![LibreSpeed Logo](https://github.com/nishith-p-shetty/speedtest/blob/master/.logo/logo3.png?raw=true)

# LibreSpeed
THIS IS A MODIFIED VERSION OF LIBRESPEED/SPEEDTEST
[YOU CAN check it out here](https://github.com/librespeed/speedtest/) 
No Flash, No Java, No Websocket, No Bullshit.

This is a very lightweight Speedtest implemented in Javascript, using XMLHttpRequest and Web Workers.

## Try it
[Take a Speedtest](https://librespeed.org)

## Compatibility
All modern browsers are supported: IE11, latest Edge, latest Chrome, latest Firefox, latest Safari.  
Works with mobile versions too.

## Features
* Download
* Upload
* Ping
* Jitter
* IP Address, ISP, distance from server (optional)
* Telemetry (optional)
* Results sharing (optional)
* Multiple Points of Test (optional)

![Screenshot](https://speedtest.fdossena.com/mpot_v6.gif)


## Server requirements
* A reasonably fast web server with Apache 2 (nginx, IIS also supported)
* PHP 5.4 (other backends also available)
* MySQL database to store test results (optional, PostgreSQL and SQLite also supported)
* A fast! internet connection

## INSTALLATION
* You will need a apache php server and sql server
* Go to php.ini file of u r apache server and edit these following
    * memory_limit=500M
    * post_max_size=500M
    * upload_max_filesize=500M
    * FIND THIS LINE ";extension=gd", REMOVE SEMICOLON "extension=gd"
    * (THESE SETTINGS WORKED GREATE FOR ME. YOU CAN REDUCE A LITTLE BIT. POST MAX SIZE SHUD BE MORE THAN 20)
* Download this repository
* ExtraCt it and put the whole folder into your WWW/html or htdocs file(WEBSITE ROOT FOLDER)
* Go to  INDEX.HTML
    * from line number 14 you have to add your server, if u have a domain add u r domain instad of EXAMPLE.COM or your port forwarded ip instead of XXX.XXX.XXX.XXX
    * scroll to bottom and paste your email instead of ENTER_YOUR_EMAIL_ADDRESS_HERE
    * and in line 402 and 405 change your title and head of webpage
* This step is only required for MySQL and PostgreSQL. If you want to use SQLite, skip to the next step.
    * Log into your database using phpMyAdmin or a similar software and create a new database. Inside the `results` folder you will find `telemetry_mysql.sql` and `telemetry_postgresql.sql`, which are templates for MySQL and PostgreSQL respectively. Import the one you need, and you will see a `speedtest_users` table in the database. You can delete the templates afterwards.
    * Open `results/telemetry_settings.php` in a text editor. Set `$db_type` to either `mysql`,`postgresql` or `sqlite`.
    * If you chose to use SQLite, you might want to change `$Sqlite_db_file` to another path where you want the database to be stored. Just make sure that the file cannot be downloaded by users. Sqlite doesn't require any additional configuration, you can skip the rest of this section.
    * If you chose to use MySQL, you must set your database credentials:
    ```php
    $MySql_username="USERNAME"; //your database username
    $MySql_password="PASSWORD"; //your database password
    $MySql_hostname="DB_HOSTNAME"; //database address, usually localhost
    $MySql_databasename="DB_NAME"; //the name of the database where you loaded telemetry_mysql.sql
    ```
    * If you chose to use PostgreSQL, you must set your database credentials:
    ```php
    $PostgreSql_username="USERNAME"; //your database username
    $PostgreSql_password="PASSWORD"; //your database password
    $PostgreSql_hostname="DB_HOSTNAME"; //database address, usually localhost
    $PostgreSql_databasename="DB_NAME"; //the name of the database where you loaded telemetry_postgresql.sql
    ```
* Inside result folder goto telementry_settings.php and edit your sql server settings and also add stats password
* See doc.md to get full information from the actual creater of libre speed

## Installation videos
* [Quick start installation guide for Ubuntu Server 19.04](https://fdossena.com/?p=speedtest/quickstart_v5_ubuntu.frag)

## Android app
A template to build an Android client for your LibreSpeed installation is available [here](https://github.com/librespeed/speedtest-android).

## Docker
A docker image is available on the [Docker Hub](https://registry.hub.docker.com/r/adolfintel/speedtest), see `doc_docker.md` for more info about it

## Go backend
A Go implementation is available in the [`speedtest-go`](https://github.com/librespeed/speedtest-go) repo, maintained by [Maddie Zhan](https://github.com/maddie).

## Node.js backend
A partial Node.js implementation is available in the `node` branch, developed by [dunklesToast](https://github.com/dunklesToast). It's not recommended to use at the moment.


