# docker-compose-lamp
sample lamp setup using Docker compose

includes **php** web server + app (phpmyadmin), **mysql** server and **nginx** server

## usage:
`docker-compose up`

## test:
* visit [`http://localhost:81/`](http://localhost:81/) and login with: myuser / mypass

* run: `docker exec dockercomposelamp_mysql_1 ping -c2 nginx`

  pings nginx container _from_ mysql, which you can see is not "linked" in docker-compose file.

### notes
You can see in the [docker-compose.yml](docker-compose.yml) file,  only port exposed to host is nginx, which uses 81 to avoid collisions with existing http. Feel free to change config options and see how they work for you.

Nginx link is simply: `proxy_pass  http://php;`

phpmyadmin used here "off-the-shelf" as an example app since it's a self-contained, well-known php app that you can also use to interact with the db. You would generally replace this with your own custom php app image based off `php:5.6-apache` (or similar).

NOTE: This is a simplified example designed for learning, not production. Use at your own peril.
