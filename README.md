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

# Running the setup

```
larasail run
```

The default configuration will install Nginx, PHP7.2, and MySQL 5.7. If you wish to use PHP7.1, you can include the argument `php71` like so:

```
larasail run php71
```


