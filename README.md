# Traefik

## Run on new Ubuntu server
### Login on root
```sh
ssh root@domain
```

### Open home directory
```sh
cd ~/
```

### Download `.env` file
```sh
wget -qO - https://raw.githubusercontent.com/kokkekpek/traefik/master/download | bash -
```

### Edit `.env` file
```sh
nano .env
```

### Change password for admin
```sh
sudo apt install apache2-utils -y
htpasswd .htpasswd admin
```
`admin:admin` by default

### Run installation script
```sh
wget -qO - https://raw.githubusercontent.com/kokkekpek/traefik/master/install | bash -
```

## Run local and manually
### Requirements
* [Docker](https://www.docker.com) `^20.x`
* [Docker Compose](https://docs.docker.com/compose) `^1.29.x`
* [GIT](https://git-scm.com)
* [apache2-utils](http://httpd.apache.org)

### Installation
```sh
git clone https://github.com/kokkekpek/traefik.git
cd traefik
cp .env.example .env
cp .htpasswd.example .htpasswd
htpasswd .htpasswd admin
docker network create web
docker compose --env-file .env up -d
```