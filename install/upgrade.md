> **DO NOT** upgrade from `1.0.x` using these instructions! Use the [Migrate from Wiki.js v1.x](/install/migrate) instructions instead. These instructions are for `2.x` installations.
{.is-danger}

> While upgrades are generally safe and it's very unlikely that it would result in data loss, **it's your responsibility to have a proper backup of your database before performing an upgrade.** Note that it's not possible to go back to a previous version of Wiki.js once the database schema has been upgraded.
{.is-warning}

# In-place Upgrade

Select your platform:

## Platforms {.tabset}

### Docker <i class="mdi mdi-docker"></i>

#### Standalone Container

Upgrading is simply a matter of recreating the container with the latest image version:

```bash
# Stop and remove container named "wiki"
docker stop wiki
docker rm wiki

# Pull latest image of Wiki.js
docker pull ghcr.io/requarks/wiki:2

# Create new container of Wiki.js based on latest image
docker run -d -p 8080:3000 --name wiki --restart unless-stopped -e "DB_TYPE=mysql" -e "DB_HOST=db" -e "DB_PORT=3306" -e "DB_USER=wikijs" -e "DB_PASS=wikijsrocks" -e "DB_NAME=wiki" ghcr.io/requarks/wiki:2
```

Check out the [Docker installation guide](/install/docker) for all the possible options when creating a Wiki.js container.

#### Docker Compose

The following commands will pull the latest image and recreate the containers defined in the docker-compose file:

```bash
docker-compose pull wiki
docker-compose up --force-recreate
```

### Linux / macOS <i class="mdi mdi-ubuntu"></i>

> The commands below assume an installation within a subfolder named `wiki`.
{.is-info}

1) Stop the running Wiki.js instance
2) Make a backup of your `config.yml` file.
  ```bash
  cp wiki/config.yml ~/config.yml.bak
  ```