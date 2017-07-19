# gogs-drone-compose

    @TODO: cannot communicate with gogs inside a drone's job


Add **gogs** and **drone** to your ```/etc/hosts```

```
# /etc/hosts
127.0.0.1    gogs.internal.cloud
127.0.0.1    drone.internal.cloud

...
```

Starts the compose

```
$ docker-compose up
```

### gogs settings

Go to ```http://gogs.internal.cloud``` to procede to the install.
* Choose Postgres
    * host : ```gogs-db:5432```
    * username & password : ```gogs```
* Change ```localhost``` to ```gogs.internal.cloud``` whenever asked
* Create an admin user with the credentials of your choice

### drone settings

Go to ```http://drone.internal.cloud```, click the login button and enter your gogs's credentials (created above).
Nothing more to do here.

### Testing

* Created a repo on gogs
* Add the repo on drone
    * go to the ```available repos``` tab, select the repo you would like to use then confirm when asked
    * check your repo's settings, webhooks must have been created.
* Commit some work and a ```.drone.yml``` file containing a simple workflow (eg. pulling a docker image)
* Waiting for gogs's hook to hit drone
* Watch and enjoy
