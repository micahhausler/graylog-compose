# Graylog in docker-compose
This `docker-compose.yml` runs all the required processes for a Graylog setup on multiple docker containers.

The following processes are run in their own docker containers

* mongodb
* elasticsearch
* graylog 1.1.4
* graylog-web 1.1.4

## Setup
This setup assumes you already have docker-compose and docker (using boot2docker) installed.

```
git clone git@github.com:micahhausler/graylog-compose.git
cd graylog-compose
docker-compose build
docker-compose up
```

Then open [https://192.168.59.103:9443/](https://192.168.59.103:9443/) and use the login

```
username: admin
password: password
```

## Security
This is NOT a production-ready setup for graylog. You'll need add TLS to [Mongo](https://docs.mongodb.org/manual/reference/configuration-options/#net-ssl-options), [Elasticsearch](https://www.elastic.co/guide/en/shield/current/reference.html#ref-ssl-tls-settings), and the [graylog server](https://gist.github.com/micahhausler/e0b1b47738ee170c6caf#file-server-conf-L56-L68), as well as fine-tune each service for your own needs. This list of measures is not comprehensive.

Be sure to:

* change the `password_secret` in `graylog/server.conf` and also add it to `graylog_web/graylog-web-interface.conf`'s `application.secret` parameter
* change the `root_password_sha2` in `graylog/server.conf`
* Add authentication to mongo, enter the parameters in `graylog/server.conf`

## License
MIT License