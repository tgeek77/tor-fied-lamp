# tor-fied-lamp
## Intro

These are docker-compose and dockerfile scripts for creating a simple vanilla lamp stack runing as a hidden service onion.

#### Special thanks to [cmehay](https://github.com/cmehay/docker-tor-hidden-service) for their projects which allowed me to build this one.

### About the scripts:
docker-compose.yml calls on three image:

*tor
*db
*apache

#### Variables

Volumes: By default, docker-compose will create a ~/.keys directory with the hostname and private key.  You can change the local directory whatevery you want

Passwords: Change the mysql root and user passwords to something other than the default passwords.  Make sure that MYSQL_PASSWORD and WORDPRESS_DB_PASSWORD are the same password as they are referring to the same thing.

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

#### Other applications

I've used this process to create several other hidden service applications such as tomcat, jboss, as well as more commonplace webservers like apache and nginx.
