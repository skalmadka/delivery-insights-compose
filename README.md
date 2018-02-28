# UrbanCode Velocity with docker-compose

## Prerequisite
1. Make sure machine is up-to date

    ```sh
    sudo apt-get update        # Fetches the list of available updates
    sudo apt-get upgrade       # Strictly upgrades the current packages
    sudo apt-get dist-upgrade  # Installs updates (new ones)
    ```

2. Install Docker https://docs.docker.com/engine/installation/

    ```sh
    $ docker --version
    Docker version 17.09.0-ce, build afdb6d4  #preferred
    ```

3. Install docker-compose https://docs.docker.com/compose/install/#install-compose

    ```sh
    $ docker-compose --version
    docker-compose version 1.8.0  #preferred
    ```

## Prepare docker volume
A docker volume is required for the MongoDB

1. Create a docker volume with name `velocity-mongo`

    ```sh
    $ docker volume create reporting-mongo
    ```

## Running the project
1. Get the docker-compose yaml file

    ```sh
    $ wget https://raw.githubusercontent.com/skalmadka/urbancode-compose/master/velocity/docker-compose.yml
    ```

2. Set the required environment variables

    ```sh
    $ export LICENSE=accept #Make sure you read LICENSE.txt and accept the terms and conditions.
    $ export ROOT_URL=http://<hostname> #URL which users will use to access the UI, usually the hostname/ip of the machine you are on.
    $ export CONSUMER_URL=http://<hostname>:6004 #URL which applications will use to access the consumer, usually the hostname/ip of the machine you are on.
    ```
3. Run

    ```sh
    $ docker-compose up -d
    ```

NOTE: To Stop/Remove. (Remove if you have a new version of any of the images. Stoping or removing the container should not affect the data as long as your volume is persistent)

    ```sh
    $ docker-compose stop
    $ docker-compose rm
    ```
