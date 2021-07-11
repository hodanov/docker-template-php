# PHP and Nginx Dev Environment on Docker

This is the php dev-environment.

The environment is using the following technologies:

- php-fpm-alpine
- xdebug
- nginx-alpine

## Requirements

This requires the following to run:

- Docker
- Docker Compose

## Getting Started

1. Clone the repo.

```
git clone git@github.com:hodanov/docker-template-php.git
```

The directory structure is the below.

```
.
├── .vscode
│   └── launch.json
├── README.md
├── df-nginx.dockerfile
├── df-php.dockerfile
├── docker-compose.yml
├── nginx
│   └── nginx.conf
└── php
    ├── app
    │   └── index.php
    ├── log
    └── php.ini
```

2. Build and run application.

```
docker-compose up -d
```

After launching containers, access the `localhost:10902`.

```
open http://localhost:10902
```

## How to debug PHP with Xdebug and VSCode

This repository has `.vscode/launch.json` and `php.ini`.

Xdebug settings are written in `php.ini`.

```
[xdebug]
xdebug.mode = debug
xdebug.start_with_request = yes
xdebug.client_host = "host.docker.internal"
xdebug.client_port = 10903
xdebug.log = "/var/log/xdebug.log"
```

The setting of VSCode are written in `.vscode/launch.json`.

```
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Listen for XDebug",
            "type": "php",
            "request": "launch",
            "port": 10903,
            "pathMappings": {
                 "/usr/src/app": "${workspaceFolder}/php/app"
             }
        },
    ]
}
```

## Author

[Hoda](https://hodalog.com)
