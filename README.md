<p align="center"><img src="https://s3.amazonaws.com/larasail/logo.svg" width="300"></p>

# LaraSail

LaraSail is a CLI tool for Laravel to help you Sail the servers of the Digital Ocean

---

You'll need a Digital Ocean Account before getting started ([Signup here](https://m.do.co/c/6e2fb7e2925f)), then you'll need to create a New Droplet. Make sure to select Ubuntu Server:

<p align="center"><img src="https://s3.amazonaws.com/larasail/ubuntu-server.png"></p>

## Installation

SSH into your server and run the following command:

```
curl -sL https://github.com/thedevdojo/larasail/archive/master.tar.gz | tar xz && source larasail-master/install
```

You can make sure it's installed by running

```
larasail -h
```

## Setup Your Laravel Server

```
larasail setup
```

The default configuration will install Nginx, PHP7.2, and MySQL 5.7. If you wish to use PHP7.1, you can include the argument `php71` like so:

```
larasail setup php71
```

## Creating a New Site

You can now Clone a Repo or Create a New Laravel app within the `/var/www` folder:

```
cd /var/www && laravel new website
```

## Setting up a new Virtual Host

You can setup a new virtual host by running:

```
larasail host website.com /var/www/website/public
```

`larasail host` accepts 2 parameters:

1. Your website domain *(website.com)*
2. The location of the files for your site *(/var/www/website/public)*

Finally, point your DNS to the IP address of your new server... And Wallah, you're ready to rock 🤘 with your new Laravel website.
