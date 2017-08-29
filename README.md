# gogs-drone-compose

### What's inside

* Consul
* Registrator
* Traefik
* Gogs + PostgreSQL
* Drone.io (server & client) + MySQL

### Why all this madness for a simple CI demonstration ?

While the use of Consul, Registrator and Traefik may seem a lot like "over-kill", they allowed me to build a completly autonomous demo. Which is really close to what a live environment would look like.

And because I was longing at such a system for a while, so why not going all the way ?

### Starts the compose

```
$ docker-compose up -d
```

### Setting up Gogs

> Still searching on how one automate this process using environement variables

Go to ```http://gogs.service.consul``` to procede to the install.
* Choose Postgres as database driver
    * host : ```gogs-db.service.consul:5432```
    * username & password : ```gogs```
* Change ```localhost``` to ```gogs.service.consul``` whenever asked
* Create an admin user with the credentials of your choice

### Setting up  Drone

Go to ```http://drone.service.consul```, click the login button and enter your gogs's credentials (created above).
Nothing more to do here.

### It's ready

* Create a repo on gogs
* Activate the repo on drone
    * Go to the ```available repos``` tab, select the repo you would like to use then confirm when asked
    * Check your repo's settings, a webhook must have been created.
* Commit some work and a ```.drone.yml``` file containing a simple workflow (eg. pulling a docker image)
* Waiting for gogs's hook to hit drone
* Watch and enjoy
