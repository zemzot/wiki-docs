# Overview

This guide is a fully detailed guide to install everything necessary to run Wiki.js on a brand new Ubuntu 18.04 / 20.04 / 22.04 LTS machine.

## What's Included

At the end of the guide, you'll have a fully working Wiki.js instance with the following components:

- Docker
- PostgreSQL 11 *(dockerized)*{.caption}
- Wiki.js 2.x *(dockerized, accessible via port 80)*{.caption}
- Wiki.js Update Companion *(dockerized)*{.caption}
- OpenSSH with UFW Firewall preconfigured for SSH, HTTP and HTTPS

# Installation

## Update the machine

First, let's make sure the machine is up to date.

```bash
# Fetch latest updates
sudo apt -qqy update

# Install all updates automatically
sudo DEBIAN_FRONTEND=noninteractive apt-get -qqy -o Dpkg::Options::='--force-confdef' -o Dpkg::Options::='--force-confold' dist-upgrade
```

## Install Docker

```bash
# Install dependencies to install Docker
sudo apt -qqy -o Dpkg::Options::='--force-confdef' -o Dpkg::Options::='--force-confold' install apt-transport-https ca-certificates curl gnupg-agent software-properties-common openssl

# Register Docker package registry
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"

# Refresh package udpates and install Docker
sudo apt -qqy update
sudo apt -qqy -o Dpkg::Options::='--force-confdef' -o Dpkg::Options::='--force-confold' install docker-ce docker-ce-cli containerd.io
```

## Setup Containers

```bash
# Create installation directory for Wiki.js
mkdir -p /etc/wiki