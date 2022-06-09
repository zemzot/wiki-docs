> Before proceeding, make sure you meet the [system requirements](/install/requirements).
{.is-info}

# Using the Docker image

Wiki.js is published as a Docker image on GitHub Packages as `ghcr.io/requarks/wiki` and on Docker Hub as `requarks/wiki`.

> It's highly recommended that you don't use the `latest` tag but instead the major version you need, e.g. `ghcr.io/requarks/wiki:2`
>
> It's also possible to point to a specific minor version (e.g. `ghcr.io/requarks/wiki:2.5`), although you will not automatically get the latest features when pulling the latest image.
{.is-info}

- View on [GitHub Packages](https://github.com/Requarks/wiki/pkgs/container/wiki)
- View on [Docker Hub](https://hub.docker.com/r/requarks/wiki)

## Environment Variables
You must set the following environment variables. They are all **required** unless specified otherwise.

### Database

- **DB_TYPE** : Type of database (`mysql`, `postgres`, `mariadb`, `mssql` or `sqlite`)
{.grid-list}

*For PostgreSQL, MySQL, MariaDB and MSSQL only:*

- **DB_HOST** : Hostname or IP of the database
- **DB_PORT** : Port of the database
- **DB_USER** : Username to connect to the database
- **DB_PASS** : Password to connect to the database
- **DB_NAME** : Database name
{.grid-list}

*When connecting to a database server with SSL enforced:*

- **DB_SSL** : Set to either `1` or `true` to enable. *(optional, off if omitted)*
- **DB_SSL_CA** : Database CA certificate content, as a single line string (without spaces or new lines), without the prefix and suffix lines. *(optional, requires 2.3+)*
{.grid-list}

*Alternative way to provide the database password, via a local file secret:*

- **DB_PASS_FILE**: Path to the mapped file containing to the database password. *(optional, replaces DB_PASS)*
{.grid-list}

*For SQLite only:*

- **DB_FILEPATH** : Path to the SQLite file
{.grid-list}

### HTTPS