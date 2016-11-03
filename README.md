# tor-fied-lamp
## Intro

These are docker-compose and dockerfile scripts for creating a simple vanilla lamp stack runing as a hidden service onion.

#### Special thanks to [cmehay](https://github.com/cmehay/docker-tor-hidden-service) for their projects which allowed me to build this one.

### About the scripts:

docker-compose.yml calls on three image:

* tor
* db
* apache

tor is the [cmehay's](https://github.com/cmehay/docker-tor-hidden-service) docker images which published the lamp stack as a .onion website.
db uses the official mariadb image from http://hub.docker.com
apache is my own image that is build but the attached dockerfile.

Dockerfile uses ubuntu:latest and installs a list of packages including apache2, php, and some standard dependancies. The list of packages can be changed or added to as needed for your own personal needs.

#### Variables

Volumes: In the tor section, docker-compose will create a ~/.keys directory with the hostname and private key.  In the apache section, it create ~/www which links to /var/www/html in the apache container. You can change these local directory whatever you want.

Passwords: **Change all passwords to something other than the default passwords!** I included a basic starter database in the configuration to ease in setting up something like wordpress or whatever.

#### Build & Run!

```
docker-compose build
docker-compose up -d
```
you can now start writing your app!

#### Stop and remove

```
docker-compose down
```

#### What's my .onion url?

Your new .onion hostname will be in ~/.keys/wordpress/hostname or you can run the following command:

```
$ docker exec -ti torfiedwordpress_tor_1 onions
```

#### Setting up LAMP applications

I have successfully
