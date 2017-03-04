# CyTube 3.0 Installation Guide

This guide will walk you through installing and configuring CyTube on a Linux server.  If you have questions, feel 
free to stop by IRC ([irc.6irc.net#cytube](http://webchat.6irc.net/?channels=cytube)).  calzoneman is the developer 
behind CyTube, but nuclearace has a lot of experience with it and can answer most of your questions if cal isn't around.

# Table of Contents
  1. [Requirements](#requirements)
  2. [Installation of prerequisites](#wiki-installation-of-prerequisites)
  3. [Installation of CyTube 3.0](#wiki-installation-of-cytube-30)
  4. [Configuration](#wiki-configuration)
  5. [Running](#wiki-running)
  6. [Maintenance](#wiki-maintenance)
  7. [Google Drive Userscript Setup](#wiki-google-drive-userscript-setup)
  8. [Importing a CyTube 2.4.6 database](#wiki-importing-a-cytube-246-database)

# Requirements

The officially supported platform for hosting a CyTube server is Linux.  I recommend Debian 8 "Jessie", but Debian 7 "Wheezy" 
or newer versions of Ubuntu (14.04 LTS or newer) work as well.  People have also run CyTube on Mac OS X, FreeBSD, and Solaris, 
although I don't test on these platforms so I cannot guarantee it will work.  **Windows is explicitly not supported.**

CyTube is relatively lightweight in terms of CPU, memory, and bandwidth usage.  However, due to the software used, it will 
not run on shared webhosting; it requires a VPS or dedicated server.  I recommend at least 256MB RAM for a small server 
(this is for both CyTube and MySQL RAM usage).  People have gotten by with less, but having sufficient RAM for MySQL to 
hold the database in memory will improve performance.

**NOTE:** while CyTube itself does not use much memory, `npm` will happily eat up gigabytes installing the dependencies.  
You may need to use alternative installers, or temporarily increase the memory for installation if using a virtual machine.

Also note that with the latest 3.0 revision, MySQL must be at least 5.5.3 to accommodate the use of the utf8mb4 character 
encoding. Some linux distros only have MySQL 5.1 available in the stock repos(CentOS 6 for example).

CyTube has a standalone webserver, so it is not necessary to use Apache or another webserver to serve content.  You may 
use a 3rd party webserver in reverse proxy mode if you wish. [cytu.be](http://cytu.be) runs nginx, which proxies back good 
requests to CyTube (and takes care of blocking bad requests and rate limiting before requests even reach CyTube).  
Configuring a reverse proxy is outside the scope of this guide.

For installation purposes I will assume you have full root access to the server, whether it be a virtual server or 
physical hardware.  I do not support installing CyTube on shared hosting platforms such as OpenShift or Heroku.

# Installation of prerequisites
## Dependencies
### Debian / Ubuntu
```sh
apt-get update && apt-get upgrade
apt-get install build-essential git python mysql-server
```

### CentOS
```sh
yum update
yum install git openssl-devel gcc-c++ mysql-server mysql mysql-devel mysql-libs
```

Please make sure that during the installation of MySQL, you choose a secure password for the root user.

## node.js

For best results, use node.js 4.x (LTS) or 5.x (stable).  v0.12.x and v0.10.x are no longer supported and will not run CyTube.
Most Debian and Red Hat based distributions do **not** include a reasonably up to date version of node.js, so I recommend 
following the instructions on https://nodejs.org/en/download/package-manager/ to install it from the third-party nodesource repo.

# Installation of CyTube 3.0

## User account

You should set up a user account that the CyTube process will run as.  Don't use root.  Just don't.  You can use your 
user account, or add a new one (there are plenty of guides on how to add a new user on your favorite distribution).

## Cloning from git

`cd` to the directory where you want your CyTube server.  Execute the following command to download the code from the Git repository:

```sh
git clone -b 3.0 https://github.com/calzoneman/sync
```

You can optionally specify a folder name after the repository URL to rename the folder something else instead of `sync`.

## NPM dependencies

```sh
cd sync
npm install
```

### npm performance

CyTube has a lot of dependencies, and some of them bring in very large dependency trees (for example, `babel`).  For this 
reason, `npm install` may attempt to consume several gigabytes of RAM and fail when running out of memory, which leads to 
errors due to an incomplete installation.  On systems with a small amount of RAM, you can try using an alternative installer 
like [`pnpm`](https://github.com/rstacruz/pnpm):

```
sudo npm install -g pnpm node-gyp
rm -rf node_modules
pnpm install
```

If this does not work, you can try using my janky little script that installs modules one at a time: 
[](https://gist.github.com/calzoneman/73929b0215cc5332367b9283fdf18aec)

# Configuration

## Database

You will need to log in to your MySQL server as root to create a user and database for CyTube:

```sh
mysql -u root -p
# ENTER PASSWORD
```

```sql
GRANT USAGE ON *.* TO cytube3@localhost IDENTIFIED BY 'super_secure_password';
GRANT ALL PRIVILEGES ON cytube3.* TO cytube3@localhost;
CREATE DATABASE cytube3;
QUIT;
```

## Configuration File

**NOTE: The configuration file is somewhat confusing and messy.  This is a known issue that I'm planning to work on.**

First, copy the template:

```sh
cp config.template.yaml config.yaml
```

Next, edit `config.yaml` with your favorite text editor.  The template is well-commented with what most of the config 
keys are for, so I will omit explaining all of them in detail, but I would like to make a few general notes:

  * The server dynamically generates links as `http://http.domain:http.port/path`.  If you want to override this, you 
  can set `http.full-address` to the desired root.  For example, http://cytu.be runs on port 8080, but I want requests 
  to go through nginx on port 80 rather than `http://cytu.be:8080`, so I have `full-address: 'http://cytu.be'` in 
  the `http` block of my configuration.
  * `http.root-domain` has to do with the way cookies work.  If your server will be accessible from multiple subdomains
  (e.g. `a.mysite.com`, `b.mysite.com`), then you must set the root domain to the common domain between them (e.g. `mysite.com`).
  * As a convention, keys called `host` specify an IP address to bind to (if your server has multiple IP addresses), and 
  keys called `domain` specify the domain name (e.g. `mysite.com`).
  * Binding a port number below 1000 requires running the server as root.  This is one of the reasons I use nginx as a reverse proxy.

# Running

Congratulations, your CyTube server is now configured!  You can launch it with `node index.js`.  On the first run, 
your server will initialize the database, log files, and channel data folders.  You should be able to connect to your 
server on the port specified.

Once you have registered your first account, you can use the following commands to assign yourself site admin rights:

```sh
mysql -u cytube3 -p
# ENTER PASSWORD
```

```sql
UPDATE `users` SET global_rank=255 WHERE name='calzoneman';
```

Any rank >= `255` has site administrator permissions.

## Persistence
There are a few options for keeping the server running after you close your SSH session:
  * `nohup node index.js &`
  * screen
  * tmux
  * [upstart](http://upstart.ubuntu.com/)

nohup, screen, and tmux are all available as packages on major distributions.  upstart is available on Ubuntu 6.10 and later.
I have also provided a simple `run.sh` script that will automatically restart the server if it crashes.  On my server, I 
launch it as `screen ./run.sh`.

### Upstart Example

First, create the configuration file.  The example below assumes you've cloned the repo to `/home/ubuntu/sync`.  Change 
this directory as necessary.

```bash
cat > /etc/init/cytube.conf << EOF
description "CyTube"

start on (filesystem and net-device-up)
stop on runlevel [!2345]

setuid ubuntu

respawn
respawn limit 2 60

chdir /home/ubuntu/sync

script
  exec /home/ubuntu/sync/run.sh
end script

emits CyTube-running 
EOF
```

Next, start the service using upstart:

```bash
sudo service cytube start
```

# Maintenance

## Git updates

CyTube is actively developed and updates frequently to fix bugs and add new features.  Git provides a convenient 
way for you to keep up with these updates.  `cd` to the directory containing CyTube, and execute `git pull` 
to retrieve the latest code.  As of September 2015, you must also run `npm install`, `npm run postinstall`, 
or `npm run build-server` to build the changes from `src/` to `lib/`.  After this, restart the server for the changes to take effect.

## Backups

You should take frequent backups in case something happens to your server.  The database and channel data can be backed up like so:

```sh
mysqldump --quick --skip-lock-tables -u cytube -psupersecretpassword cytube > my_database_backup.sql
tar cjf my_channels_backup.tar.bz2 chandump
```

# Google Drive Userscript Setup

In response to increasing difficulty and complexity of maintaining Google Drive
support, the native player has been phased out in favor of requiring a
userscript to allow each client to fetch the video stream links for themselves.
Users will be prompted with a link to `/google_drive_userscript`, which explains
the situation and instructs how to install the userscript.

As a server admin, you must generate the userscript from the template by using
the following command:

```sh
npm run generate-userscript <site name> <url> [<url>...]
```

The first argument is the site name as it will appear in the userscript title.
The remaining arguments are the URL patterns on which the script will run.  For
example, for cytu.be I use:

```sh
npm run generate-userscript CyTube http://cytu.be/r/* https://cytu.be/r/*
```

This will generate `www/js/cytube-google-drive.user.js`.

# Importing a CyTube 2.4.6 database

CyTube 3.0 uses a slightly different database format than previous versions.  I have provided an import script which 
will copy data over to the new format.

First, create a new database for CyTube 3:

```sh
mysql -u root -p
# ENTER PASSWORD
```

```sql
GRANT ALL PRIVILEGES ON cytube3.* TO cytube@localhost;
CREATE DATABASE cytube3;
QUIT;
```

Next, run `import.js`:

```sh
node import.js | tee output.txt
```

The `| tee output.txt` saves all console output to a file so you can inspect it for errors if necessary.  Enter 
the appropriate database details, and wait for the script to import.  It will log everything it imports.

Copy the `chandump` folder from your old CyTube Directory to your CyTube 3 folder.

Once the import script has finished, you can begin using CyTube 3.  Be sure to inspect for errors before you delete 
any data from your CyTube 2 database!

[Back to Quick Reference](index.md)
