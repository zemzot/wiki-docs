# Overview

The DigitalOcean Marketplace Wiki.js image is a pre-configured environment, made by the developers of Wiki.js, containing everything you need to get started with Wiki.js.

## Image Specifications

Ubuntu 20.04 LTS with the following software pre-installed:

- Docker
- PostgreSQL 11 *(dockerized)*{.caption}
- Wiki.js 2.x *(dockerized, accessible via port 80)*{.caption}
- Wiki.js Update Companion *(dockerized)*{.caption}
- OpenSSH with UFW Firewall preconfigured for SSH, HTTP and HTTPS

## Droplet Size

Wiki.js works great on even the smallest Droplet size (**1GB RAM + 1 CPU**).

However, for best performance, we recommend using at least the **2GB RAM + 2 CPU** droplet size. Wiki.js use background processes for CPU intensive tasks (e.g. page rendering). Therefore, having at least 2 CPU cores will results in improved performance for such tasks.

Note that you can always upgrade to a more powerful droplet configuration in the future from the DigitalOcean control panel.

# Getting Started

1. Go to the [**Wiki.js**](https://marketplace.digitalocean.com/apps/wiki-js?refcode=5f7445bfa4d0) listing in the DigitalOcean Marketplace and click **Create Wiki.js Droplet**.
1. Select a droplet size, datacenter region and additional options.
1. Click **Create droplet** once you entered all necessary info.
1. Wait for the droplet to be created.
1. Click on the newly created droplet and copy the **public IP** address.
1. In a new browser tab, navigate to http://YOUR-PUBLIC-IP *(replace with your IP)*
  > **It can take several minutes before the server starts accepting requests.** Various services must initialize for the first time before you'll be able to access your wiki. If it doesn't load on first attempt, wait 5 minutes and try again.
  {.is-info}
8. A setup screen for Wiki.js should appear. Enter the desired **email address** and **password** for the administrator account.
1. Enter the **full URL** to your wiki, without the trailing slash. It's recommended to point a sub-domain / domain to your public IP (e.g. wiki.example.com). If you don't have a domain setup yet, you can use your public IP as the URL (e.g. http://xx.xx.xx.xx). This can be changed later in the **Administration Area** (under the **General** section).
1. Click on **Install** to complete the installation. You'll automatically be redirected to the login page once completed. Enter the email and password for the administrator account you entered earlier.

# Automatic HTTPS with Let's Encrypt

> You must complete the setup wizard (see [Getting Started](#getting-started)) **BEFORE** enabling Let's Encrypt!
{.is-warning}

1. Create an **A record** on your domain registrar to point a domain / sub-domain (e.g. wiki.example.com) to your droplet **public IP**.
2. Make sure you're able to load your wiki using that domain / sub-domain on HTTP (e.g. http://wiki.example.com).
3. Connect to your droplet via **SSH**.
4. **Stop** and **remove** the existing wiki container *(no data will be lost)* by running the commands below:

```bash
docker stop wiki
docker rm wiki
```