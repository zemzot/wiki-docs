# Overview

The AWS Marketplace Wiki.js image is a pre-configured environment, made by the developers of Wiki.js, containing everything you need to get started with Wiki.js.

## Image Specifications

Ubuntu 18.04 LTS with the following software pre-installed:

- Docker
- PostgreSQL 11 *(dockerized)*{.caption}
- Wiki.js 2.x *(dockerized, accessible via port 80)*{.caption}
- Wiki.js Update Companion *(dockerized)*{.caption}
- OpenSSH with UFW Firewall preconfigured for SSH, HTTP and HTTPS

## Instance Type

Wiki.js requires at least the **t3.micro** instance size. *The **t3.nano** instance type is not supported.*{.red--text}

However, for best performance, we recommend using at least the **t3.small** or preferrably the **c5.large** instance size. Wiki.js use background processes for CPU intensive tasks (e.g. page rendering). Therefore, having at least 2 dedicated CPU cores will results in improved performance for such tasks.

# Getting Started

1. From the [Wiki.js Product Page](https://aws.amazon.com/marketplace/pp/B0832LDTKQ) on AWS Marketplace, click the **Continue to subscribe** button located at the top of the page.
1. Follow the on-screen instructions to launch an instance.
1. Once the instance is running, go to the instance details in the AWS Management Console.
1. Copy the **Public DNS** endpoint for your instance.
1. In a new browser tab, navigate to http://YOUR-PUBLIC-DNS *(replace with your Public DNS endpoint or IP)*
  > **It can take several minutes before the server starts accepting requests.** Various services must initialize for the first time before you'll be able to access your wiki. If it doesn't load on first attempt, wait 5 minutes and try again.
  {.is-info}
6. A setup screen for Wiki.js should appear. Enter the desired **email address** and **password** for the administrator account.
1. Enter the **full URL** to your wiki, without the trailing slash. It's recommended to point a sub-domain / domain to your public IP (e.g. wiki.example.com). If you don't have a domain setup yet, you can use your public DNS endpoint or IP as the URL (e.g. http://xx.xx.xx.xx). This can be changed later in the **Administration Area** (under the **General** section).
1. Click on **Install** to complete the installation. You'll automatically be redirected to the login page once completed. Enter the email and password for the administrator account you entered earlier.

# Automatic HTTPS with Let's Encrypt

> You must complete the setup wizard (see [Getting Started](#getting-started)) **BEFORE** enabling Let's Encrypt!
{.is-warning}

1. Create an **A record** on your domain registrar to point a domain / sub-domain (e.g. wiki.example.com) to your EC2 instance **public IP**.
2. Make sure you're able to load your wiki using that domain / sub-domain on HTTP (e.g. http://wiki.example.com).
3. Connect to your EC2 instance via **SSH**.
4. **Stop** and **remove** the existing wiki container *(no data will be lost)* by running the commands below:

```bash
docker stop wiki
docker rm wiki
```

5. Run the following command by replacing the `wiki.example.com` and `admin@example.com` values with **your own domain / sub-domain** and the **email address** of your wiki administrator: