[![Go Report Card](https://goreportcard.com/badge/github.com/savsgio/microservice-email)](https://goreportcard.com/report/github.com/savsgio/microservice-email)

microservice-email
==================

Microservice to send emails


#### System Dependencies

- [Go](https://golang.org/dl/) (>= 1.9)
- [Dep (Dependency management for Go)](https://golang.github.io/dep/)
- [RabbitMQ](https://www.rabbitmq.com/)
- make

#### Go dependencies

- [fasthttp](https://github.com/valyala/fasthttp)
- [fasthttprouter](https://github.com/buaazp/fasthttprouter)
- [amqp](https://github.com/streadway/amqp)
- [gomail](https://github.com/go-gomail/gomail)
- [yaml](https://github.com/go-yaml/yaml)
- [go-logger](https://github.com/savsgio/go-logger)


General
-------

Optimize Go code:
```bash
make simplify
```

Download Go dependencies and build:
```bash
make
```

Run:

Copy `etc/config.yml` to `etc/config.dev.yml` *(this file not tracked in Git)*, modify each config and exec:
```bash
make run
```

***Note:*** If you want to use with Docker, make sure you have this rabbitmq configuration in `etc/config.dev.yml`:
```yaml
...
rabbitmq:
  host: rabbitmq_server
  user: guest
  password: guest
  ...
...
```

Installation
------------

```bash
make install
```

After, you can exec with
```bash
microservice-email
```

Optional arguments:
- `-log-level`: Level of log that you want to show (default: *info*)
- `-config-file`: Path of configuration file (default: */etc/microservice-email.yml*)
- `-version`: Print version of service

#### API:

This API only accept ***POST*** http request with below parameters in body:

Explanation (all are required):

- `to`: List of emails of destiny
- `subject`: Subject of email
- `content_type`: Content type of email that it can be ***text/plain*** or ***text/html***
- `body`: Content of email

Example of request to send a email:

```json
{
  "to": ["example_1@example.com", "example_2@example.com"],
  "subject": "Hi, my friend",
  "content_type": "text/html",
  "body": "<h1>This is the body of my Email in HTML format</h1>"
}
```

Docker
------

#### Dependencies

- [Docker](https://www.docker.com/)
- [Docker-compose](https://docs.docker.com/compose/) *Recommended to install with `pip3` (python3)*

Run:
```bash
make docker_run
```

Others
------

**Feel free to contribute it or fork me...** :wink:
