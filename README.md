<p align="center"><img src="https://s3.amazonaws.com/larasail/logo.svg"></p>

# LaraSail

LaraSail is a CLI tool for Laravel to help you Sail the servers of the Digital Ocean

To Install boot up a new Ubuntu server on Digital Ocean and run the following command:

```
curl -sL https://github.com/thedevdojo/larasail/archive/master.tar.gz | tar xz && source larasail-master/install
```

You can make sure it's installed by running

```
larasail -h
```

in the command line.

# Running the setup

```
larasail run
```

The default configuration will install Nginx, PHP7.2, and MySQL 5.7. If you wish to use PHP7.1, you can include the argument `php71` like so:

```
larasail run php71
```


