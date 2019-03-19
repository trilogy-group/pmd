# Development with Devspaces

### Install DF Devspaces

Create and install devspaces client as it is written in help guide https://support.devspaces.io/article/22-devspaces-client-installation.

Here are some details about DF Devspaces https://devspaces.io/devspaces/help

Here follows the main commands used in Devspaces cli.

|action   |Description                                                                                   |
|---------|----------------------------------------------------------------------------------------------|
|`devspaces --help`                    |Check the available command names.                               |
|`devspaces create [options]`          |Creates a DevSpace using your local DevSpaces configuration file |
|`devspaces start <devSpace>`          |Starts the DevSpace named \[devSpace\]                           |
|`devspaces bind <devSpace>`           |Syncs the DevSpace with the current directory                    |
|`devspaces info <devSpace> [options]` |Displays configuration info about the DevSpace.                  |

Use `devspaces --help` to know about updated commands.

### Devspaces Notes

You should have Devspaces cli services started and logged to develop with Devspaces.

All devspaces and docker cli commands should be issued from **project directory**.

Your **project dicrectory**  will be bound to remote `/data` directory in remote Devspace.

### Devspaces Development


1 - Create Devspaces

```bash
cd devspaces/docker
devspaces create
cd ../../
```

2 - Start containers

```bash
devspaces start pmd
```

3 - Synchronize containers

```bash
devspaces bind pmd
```

4 - Grab some container info

```bash
devspaces info pmd
```

5 - Connect to development container

```bash
devspaces exec pmd
```

6 - Build and test application

Follow steps described in **Build and Test PMD** section.

### Build and Test PMD

1 - Build and Test application

```bash
./mvnw clean verify

```

2 - Verify generated distribution files

```bash
cd pmd-dist/target
ls *.zip
```

### Docker Script Manager (CLI)

We added a convenience script to ease `docker-compose` usage:

```bash
devspaces/docker-cli.sh <command>

```

Currently, we have these commands:

|action    |Description                                                               |
|----------|--------------------------------------------------------------------------|
|`build`   |Builds images                                                             |
|`deploy`  |Deploy Docker compose containers                                          |
|`undeploy`|Undeploy Docker compose containers                                        |
|`start`   |Starts Docker compose containers                                          |
|`stop`    |Stops Docker compose containers                                           |
|`exec`    |Get into the container                                                    |


#### Docker cli steps

1 - Build and Run local containers.

```bash
devspaces/docker-cli.sh build
devspaces/docker-cli.sh deploy
devspaces/docker-cli.sh start
```

2 - Get into container

```bash
devspaces/docker-cli.sh exec
```

3 - Build and test application

Follow steps described in **Build and Test PMD** section.
