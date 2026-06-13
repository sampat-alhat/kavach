# kavanch
# Web Application Test Environment Setup

This project uses Docker Compose to deploy two intentionally vulnerable web applications used for security testing:

* DVWA (Damn Vulnerable Web Application)
* OWASP Juice Shop

## Prerequisites

Verify Docker and Docker Compose are installed:

```bash
docker --version
docker compose version
```

Start Docker service:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```

Verify Docker is running:

```bash
docker run hello-world
```

## Directory Structure

```text
webapp/
└── env/
    └── docker-compose.yml
```

## Create docker-compose.yml

Create the file `webapp/env/docker-compose.yml` with the following content:

```yaml
services:
  dvwa:
    image: vulnerables/web-dvwa
    container_name: dvwa
    ports:
      - "8080:80"
    restart: unless-stopped

  juice-shop:
    image: bkimminich/juice-shop
    container_name: juice-shop
    ports:
      - "3000:3000"
    restart: unless-stopped
```

## Start the Environment

Navigate to the environment directory:

```bash
cd webapp/env
```

Start all containers:

```bash
docker compose up -d
```

Verify containers are running:

```bash
docker ps
```

Expected containers:

* dvwa
* juice-shop

## Access Applications

DVWA:

```text
http://localhost:8080
```

OWASP Juice Shop:

```text
http://localhost:3000
```

## View Logs

DVWA:

```bash
docker logs dvwa
```

Juice Shop:

```bash
docker logs juice-shop
```

Follow live logs:

```bash
docker compose logs -f
```

## Stop Environment

```bash
docker compose down
```

## Remove Containers and Images

```bash
docker compose down --rmi all
```

## Reproducibility

A reviewer can reproduce the web application assessment environment by:

1. Installing Docker and Docker Compose.
2. Cloning the repository.
3. Navigating to `webapp/env`.
4. Running `docker compose up -d`.
5. Accessing DVWA on port 8080 and Juice Shop on port 3000.

The environment should be operational within 15 minutes on a standard laptop.

