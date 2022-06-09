Before going any further, make sure your system meets all the [requirements](/install/requirements).

> Looking for a complete, easy step-by-step installation guide, including all dependencies and an auto-updater? Check out the [Ubuntu-based](/install/ubuntu) installation guide.
{.is-info}

# Install

1. Download the latest version of Wiki.js:
  ```bash
  wget https://github.com/Requarks/wiki/releases/latest/download/wiki-js.tar.gz
  ```
2. Extract the package to the final destination of your choice:
  ```bash
  mkdir wiki
  tar xzf wiki-js.tar.gz -C ./wiki
  cd ./wiki
  ```
3. Rename the sample config file to `config.yml`:
  ```bash
  mv config.sample.yml config.yml
  ```
4. Edit the config file and fill in your database and port settings ([Configuration Reference](/install/config)):
  ```bash
  nano config.yml
  ```
5. ***For SQLite installations only:*** *(skip this step otherwise)* Fetch native bindings for SQLite3:
  ```bash
  npm rebuild sqlite3
  ```
6. Run Wiki.js
  ```bash
  node server
  ```
7. Wait until you are invited to open to the setup page in your browser.
8. Complete the setup wizard to finish the installation.

# Run as service

There are several solutions to run Wiki.js as a background service. We'll focus on **systemd** in this guide as it's available in nearly all linux distributions.

1. Create a new file named `wiki.service` inside directory `/etc/systemd/system`.
  ```bash
  nano /etc/systemd/system/wiki.service
  ```
2. Paste the following contents (assuming your wiki is installed at `/var/wiki`):
  ```ini
  [Unit]
  Description=Wiki.js
  After=network.target