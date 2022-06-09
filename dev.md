Wiki.js is fully modular, which allows any developer to write their own module.

There are 3 methods to develop for Wiki.js. You can either use the dockerized development environment for VS Code *(recommended)*, a generic docker environment or install all dependencies manually on your machine.

# Using Docker + Visual Studio Code

## Prerequisites

* Docker
* Docker Compose
* Linux / macOS / Windows 10 Pro or Enterprise
* Visual Studio Code

## Running the project
1. Clone the project from [GitHub](https://github.com/Requarks/wiki).
2. Open the project folder in **Visual Studio Code**
3. From the **Extensions** tab, install the **Remote Development** extension by Microsoft (*ms-vscode-remote.vscode-remote-extensionpack*)
4. Click the **green button** located in the bottom-left corner of VS Code: *(or open the command palette)*
	![ui-dev-vscode-remotebtn.png](/assets/ui/ui-dev-vscode-remotebtn.png =350x){.radius-5 .decor-shadow .ml-5}
5. Select **Remote Containers - Reopen in Container**
6. VS Code will now reload and start initializing the containers. Wait for it to complete. This **may take a while the very first time** as npm dependencies must be installed.
	![ui-dev-vscode-init.png](/assets/ui/ui-dev-vscode-init.png =500x){.radius-5 .decor-shadow .ml-5}
7. Open the **Terminal** *(View > Terminal)* and select "**1: bash**" from the dropdown selector on the right:
	![ui-dev-vscode-bash.png](/assets/ui/ui-dev-vscode-bash.png =400x){.radius-5 .decor-shadow .ml-5}
8. From the command line, type the following command to start Wiki.js in development mode:
    ```bash
      yarn dev
    ```
9. Wait for the initialization to complete. You'll be prompted to load **http://localhost:3000/** when ready.
9. Browse to **http://localhost:3000/** _(replace localhost with the hostname of your machine if applicable)_.
10. Complete the setup wizard to finish the installation.

## Stopping the project

Click on **File > Close Remote Connection** to stop the containers and close the Visual Studio Code instance.

## Removing the containers

When you're done and no longer need the development environment, open the **Remote Explorer** tab and remove all containers starting with the name `wiki`.

Alternatively, see the [generic method](#removing-the-containers-1) below.

# Using Docker (Generic)

## Prerequisites

* Docker
* Docker Compose
* Linux / macOS / Windows 10 Pro or Enterprise