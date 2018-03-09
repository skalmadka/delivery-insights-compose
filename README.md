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

4. Your UrbanCode Velocity license key. Get one for FREE from the UrbanCode Velocity registration site. <br/> http://di-kube.us-south.containers.mybluemix.net:32018/

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

2. Set the required environment variables. You can edit other parameters by making a change directly in the `docker-compose.yml` file.

    ```sh
    $ export LICENSE_KEY=<velocity-license-key> #Your UrbanCode Velocity license key.
    $ export URL_DOMAIN=<hostname> #This is usually the hostname of the machine this app is running on. Do NOT include http, port numbers or trailing "/", just the hostname.
    $ export ENCRYPT_KEY=<a-unique-guid/string-for-data-encryption> #A unique id used to encrypt user names, tokens and any email addresses in mongoDB.
    ```

3. Run

    ```sh
    $ docker-compose up -d
    ```

4. Admin logs in to `http://${URL_DOMAIN}/admin` to set up UCD integrations and user authentication mechanism. After that, users can login to `http://${URL_DOMAIN}/home` to view reports.

## Uninstalling the release

NOTE: To Stop/Remove. (Remove if you have a new version of any of the images. Stoping or removing the container should not affect the data as long as your volume is persistent)

  ```sh
  $ docker-compose stop
  $ docker-compose rm
  ```
