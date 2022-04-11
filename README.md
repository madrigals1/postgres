# Postgres + PgAdmin4

Postgres + PgAdmin 4 with my settings. This project lets you manage your **postgres** instance through **pgAdmin4** instance, optionally available through HTTPS over the internet.

## Prerequisites

Make sure you have installed these:
- [Docker and Docker Compose](https://phoenixnap.com/kb/install-docker-compose-on-ubuntu-20-04) - Will install all the required packages and software.
- (Optional) [Dockerized Nginx](https://github.com/madrigals1/nginx_proxy_manager) - Will generate SSL certificates and make the app accessible through `HTTPS_NETWORK`, that is set inside `.env`.

## Installation

Make a copy of `.env.example` file named `.env`

```shell script
cp .env.example .env
```

---

Environment variables:
- **Postgres** settings:
    - `POSTGRES_DEFAULT_DB` - default database name
    - `POSTGRES_DEFAULT_USER` - default user, that has admin access default database
    - `POSTGRES_DEFAULT_PASSWORD` - password for default user
    - `POSTGRES_PORT` - port on which **Postgres** instance will be running.
- **PgAdmin4** settings:
    - `PGADMIN_PORT` - port, on which **pgAdmin4** instance will be running.
- `HTTPS_NETWORK` - network, in which our **Dockerized Nginx** is running. 
- `DATABASE_NETWORK` - network, on which our database will be accessible.

```dotenv
# Postgres settings
POSTGRES_DEFAULT_DB=postgres
POSTGRES_DEFAULT_USER=admin
POSTGRES_DEFAULT_PASSWORD=password
POSTGRES_PORT=5432

# pgAdmin settings
PGADMIN_PORT=8765

# Nginx proxy settings
HTTPS_NETWORK=https_network
DATABASE_NETWORK=database_network
DEFAULT_EMAIL=user@example.com
```

---

Create network with the name, that we have in `HTTPS_NETWORK` environment variable.

```shell script
docker network create https_network
```

Create network with the name, that we have in `DATABASE_NETWORK` environment variable.

```shell script
docker network create database_network
```

---

Build the Docker image

```shell script
docker-compose build
```

## Running

Start
```
docker-compose up
```

Stop
```
docker-compose down
```

## Usage

- Access **pgAdmin4** instance through      `localhost:PGADMIN_PORT` from browser or create **SSL Certificate** and **Proxy Host** using [Dockerized Nginx](https://github.com/madrigals1/nginx_proxy_manager)

## Authors
- Adi Sabyrbayev [Github](https://github.com/madrigals1), [LinkedIn](https://www.linkedin.com/in/madrigals1/)