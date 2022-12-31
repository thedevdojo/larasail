<p align="center"><img src="https://s3.amazonaws.com/larasail/logo.svg" width="300"></p>

# LaraSail

LaraSail is a CLI tool for Laravel to help you sail the servers of the [DigitalOcean](https://digitalocean.com/).

<p align="center"><img src="https://s3.amazonaws.com/larasail/larasail-command.png"></p>

---

You'll need a DigitalOcean account before getting started ([Signup here](https://m.do.co/c/6e2fb7e2925f)), then you'll need to create a `New Droplet`. Make sure to select Ubuntu Server:

<p align="center"><img src="https://user-images.githubusercontent.com/21223421/194825321-c91e059f-a862-481e-a928-4f9d7ebce08e.png"></p>

## Installation

SSH into your server and run the following command:

```
curl -sL https://github.com/thedevdojo/larasail/archive/master.tar.gz | tar xz && source larasail-master/install
```

You can make sure it's installed by running:

```
larasail -h
```

## Setup your server

```
larasail setup
```

The default configuration will install `Nginx`, `PHP 8.0`, and `MySQL 8`. If you wish to use PHP `7.1`, `7.2`, `7.3`, `7.4`, `8.1` or `8.2` you can include the argument `php71`/`php72`/`php73`/`php74`/`php81`/`php82` like so:

```
larasail setup php71 # Install with PHP 7.1
larasail setup php72 # Install with PHP 7.2
larasail setup php73 # Install with PHP 7.3
larasail setup php74 # Install with PHP 7.4
larasail setup php81 # Install with PHP 8.1
larasail setup php82 # Install with PHP 8.2
```

### Database

By default, LaraSail will set up the latest version of MySQL. To opt for MariaDB instead, kindly pass `mariadb` to `larasail setup` as the second or third parameter like so:

```
larasail setup mariadb # will install default PHP version (7.4) and MariaDB
larasail setup php80 mariadb # will install the selected PHP version (8.0 in this case) and MariaDB
larasail setup mariadb php80 # same as above

```

### Redis
By default, LaraSail does not install a Redis server. To opt to install `redis`, pass `redis` option to `larasail setup` as the second or third parameter like so:

```shell
larasail setup php80 redis
```

or

```shell
larasail setup redis
```

## Creating a new site

### :sparkles: Automatically

#### Laravel

After setting up the server you can create a new project by running:

```
larasail new <project-name> [--jet <livewire|inertia>] [--teams] [--www-alias]
```

This will automatically create a project folder in `/var/www` and set up a host if the provided project name contains periods (they will be replaced with underscores for the directory name). By default, LaraSail sets up the Nginx site configuration and [Let’s Encrypt](https://letsencrypt.org/) SSL certificate for your domain. If you would like both the `www` alias and root domain setup (i.e. `example.com` and `www.example.com`) kindly pass the `--www-alias` flag.

#### Wave

[Wave](https://github.com/thedevdojo/wave) - The Software as a Service Starter Kit, designed to help you build the SAAS of your dreams. :rocket: :moneybag:
LaraSail allows you to create a new Wave project automatically by adding `--wave` flag to the `new` command as follows:

```
larasail new <project-name> [--wave]
```

Just like Laravel above, this will create a project folder, setup the Nginx site configuration and Let’s Encrypt SSL certificate for your domain. By default, you will be prompted to create a project database and if successful, will migrate and seed the database.

### :construction: Manually

Alternatively, you can clone a repository or create a new Laravel app within the `/var/www` folder:

```
cd /var/www && laravel new mywebsite
```

If you want to include [Laravel Jetstream](https://jetstream.laravel.com/) into your project, you need to specify the `--jet` option:

```
cd /var/www && laravel new mywebsite --jet
```

Then, you'll need to setup a new Nginx host by running:

```
larasail host mywebsite.com /var/www/mywebsite --www-alias
```

`larasail host` accepts three parameters:

1. Your website domain *(mywebsite.com)*
2. The location of the files for your site *(/var/www/mywebsite/public)*
3. Optional flag if you would like to include your project's `www` alias: `www.mywebsite.com` *(--www-alias)*

Finally, point your domain to the IP address of your new server. And wallah, you're ready to rock 🤘 with your new Laravel website. If you used the `--www-alias` flag, don't forget to add your domain's www `CNAME` record

## Passwords

When installing and setting up LaraSail there are two passwords that are randomly generated:

1. The password for the `larasail` user created
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

## Creating a database

After you have created your project you can create a database and user for it by using the following command:

```
larasail database init [--user larasail] [--db larasail] [--force]
```

By default it will create a database and the user `larasail` and grant all permissions to that user.

**TIP**: If you are in the project directory when you run this command, it will also try to update the `.env` file
with the newly generated credentials.

After you have created a database, you can show the newly generated passwords using the following command:

```
larasail database pass
```

## Switching to the larasail user

When you SSH into your server you may want to switch users back to the `larasail` user, you can do so with the following command:

```
su - larasail
```

Make sure to star this repository and watch it for future updates. Thanks for checking out LaraSail. ⛵

## Contributing

If you are contributing, please read the [contributing file](CONTRIBUTING.md) before submitting your pull requests.
