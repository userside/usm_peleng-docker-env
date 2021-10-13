# USM_PELENG Docker Environment

This environment provides the feature of running the usm_peleng module inside the Docker container. This environment **does not contain** the module itself. You should download it additionally in your account and copy it inside the environment as described below.

1. Download last version of docker-environment to your server from https://github.com/userside/usm_peleng-docker-env/releases
2. Unzip downloaded archive to folder `usm_peleng-docker-env` and copy `usm_peleng` folder from unzipped folder into **userside bundle** folder. You should get approximately the following bundle file structure:
  ```
  /docker
   └── userside
        ├── config
        ├── data
        ├── usm_peleng
        │    ├── log
        │    ├── module
        │    │    └── usm_peleng.conf
        │    ├── cpanfile
        │    └── Dockerfile
        ├── docker-compose.yml
        ├── init.sh
        ├── Makefile
        └── README.md
  ```
3. From `usm_peleng-docker-env/docker-composer.yml` copy the whole service config `usm_peleng:...` to service block into your docker-compose.yml. **Pay attention to the formatting!** The indents in the yaml file are very important.
  ```yaml
  services:
    postgres:
      ...
    
    fpm:
      ...
    
    ...(other services)...

    usm_peleng:
      build:
        context: ${USERSIDE_BASE_DIR}/usm_peleng
      environments:
        USERSIDE_API_KEY: 'api-secret-key'
      volumes:
        - ${USERSIDE_BASE_DIR}/usm_peleng/module:/app
        - ${USERSIDE_BASE_DIR}/usm_peleng/log:/var/log/usm_peleng
        - /etc/localtime:/etc/localtime:ro
        - /etc/timezone:/etc/timezone:ro
      networks:
        - internal

  volumes:
    ...
  ```
4. Setup environments.
5. Download **usm_peleng** module from https://my.userside.eu/, extract and copy **only one file** `usm_peleng.pl` to the subdirectory `usm_peleng/module` folder. It should turn out as follows:
  ```
  /docker
   └── userside
        ├── config
        ├── data
        ├── usm_peleng
        │    ├── log
        │    ├── module
        │    │    ├── usm_peleng.conf
        │    │    └── usm_peleng.pl
        │    ├── cpanfile
        │    └── Dockerfile
  ```
6. Go to folder `/docker/userside` then build docker-image for service usm_peleng. It can take a long time, but it only needs to be done once.
  ```bash
  sudo docker-compose build usm_peleng
  ```
8. Make a test run:
  ```bash
  sudo docker-compose run --rm usm_peleng
  ```

9. Add a line to your /etc/cron.d/userside similar to the others. For example:
  ```
  * * * * *    root    /usr/local/bin/docker-compose .... run --rm usm_peleng > /dev/null
  ```

### Any questions?

All questions are accepted only through the ticket system of your account.