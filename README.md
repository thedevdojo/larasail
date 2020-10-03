<p align="center"><img src="https://s3.amazonaws.com/larasail/logo.svg" width="300"></p>

# LaraSail

LaraSail is a CLI tool for Laravel to help you Sail the Servers of the DigitalOcean

<p align="center"><img src="https://s3.amazonaws.com/larasail/larasail-command.png"></p>

---

You'll need a DigitalOcean Account before getting started ([Signup here](https://m.do.co/c/6e2fb7e2925f)), then you'll need to create a New Droplet. Make sure to select Ubuntu Server:

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

The default configuration will install Nginx, PHP 7.4, and MySQL 5.7. If you wish to use PHP 7.1, PHP 7.2, or PHP 7.3, you can include the argument `php71`/`php72`/`php73` like so:

```
larasail setup php71 # Install with PHP 7.1
larasail setup php72 # Install with PHP 7.2
larasail setup php73 # Install with PHP 7.3
```

## Creating a New Site

### :sparkles: Automatically

After setting up the server you can create a new project automatically by running:

```
larasail new <project-name> [--jet <livewire|inertia>] [--teams]
```

This will automatically create a project folder in `/var/www` and set up a host if provided project name contains periods (they will be replaced with underscores for the directory name).

### :construction: Manually

Alternatively, you can Clone a Repo or Create a New Laravel app within the `/var/www` folder:

```
cd /var/www && laravel new mywebsite
```

Then, you'll need to setup a new Nginx Host by running:

```
larasail host mywebsite.com /var/www/mywebsite
```

`larasail host` accepts 2 parameters:

1. Your website domain *(website.com)*
2. The location of the files for your site *(/var/www/website/public)*

Finally, point your Domain to the IP address of your new server... And Wallah, you're ready to rock 🤘 with your new Laravel website.

## Passwords

When installing and setting up Larasail there are 2 passwords that are randomly generated.

1. The password for the new larasail user created on the server.
2. The default MySQL password

To get the `larasail` user password you can type in the following command:

```
larasail pass
```

And the password for the `larasail` user will be displayed. Next, to get the default MySQL root password you can type the following command:

```
larasail mysqlpass
```

And the MySQL root password will be displayed.

## Switching to Larasail user

When you SSH into your server you may want to Switch Users back to the larasail user, You can do so with the following command:

```
su - larasail
```

Make sure to star this repo and watch this repo for future updates. Thanks for checking out Larasail ⛵

## Contributing

If you are contributing, please read the [contributing file](CONTRIBUTING.md) before submitting your pull requests.