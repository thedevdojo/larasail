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
larasail setup php80 # Install with PHP 8.0
```
### Database

By default, larasail will setup the latest version of MySQL. To opt for MariaDB instead, kindly pass `mariadb` to `larasail setup` as the second or third parameter like so:

```
larasail setup mariadb # will install default php version (7.4) and MariaDB
larasail setup php80 mariadb # will install the selected php version (8.0 in this case) and MariaDB
larasail setup mariadb php80 # same as 2 above

```

## Creating a New Site

### :sparkles: Automatically

After setting up the server you can create a new project automatically by running:

```
larasail new <project-name> [--jet <livewire|inertia>] [--teams] [--www-alias]
```

This will automatically create a project folder in `/var/www` and set up a host if provided project name contains periods (they will be replaced with underscores for the directory name).
By default, larasail sets up the Nginx site configuration and Letsencrypt SSL certificate for your domain. If you would like both the `www` alias and root domain setup (i.e `example.com` and `www.example.com`) kindly pass the `--www-alias` flag.

### :construction: Manually

Alternatively, you can Clone a Repo or Create a New Laravel app within the `/var/www` folder:

```
cd /var/www && laravel new mywebsite
```

If you want to include [Laravel Jetstream][https://jetstream.laravel.com/) into your project, you need to specify the `--jet` option:

```
cd /var/www && laravel new mywebsite --jet
```

Then, you'll need to setup a new Nginx Host by running:

```
larasail host mywebsite.com /var/www/mywebsite --www-alias
```

`larasail host` accepts 3 parameters:

1. Your website domain *(mywebsite.com)*
2. The location of the files for your site *(/var/www/mywebsite/public)*
3. Optional flag if you would like to include your project's `www` alias: `www.mywebsite.com` *(--www-alias)*

Finally, point your Domain to the IP address of your new server... And Wallah, you're ready to rock 🤘 with your new Laravel website.
If you used the `--www-alias` flag, don't forget to add your domain's www `CNAME` record

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

## Creating database

After you have created your project you can create additional database and user for it using the following command:

```
larasail database init [--user larasail] [--db larasail] [--force]
```

By default it will create user and database `larasail` and grant all permissions to that user.

**TIP**: If you are in the project directory when you run this command, it will also try to update `.env` file
with newly generated credentials.

After you have created databases, you can show newly generated passwords using the following command:

```
larasail database pass
```

## Switching to Larasail user

When you SSH into your server you may want to Switch Users back to the larasail user, You can do so with the following command:

```
su - larasail
```

Make sure to star this repo and watch this repo for future updates. Thanks for checking out Larasail ⛵

## Contributing

If you are contributing, please read the [contributing file](CONTRIBUTING.md) before submitting your pull requests.
