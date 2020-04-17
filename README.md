# USM_PELENG Docker Environment

This environment provides the feature of running the usm_peleng module inside the Docker container. This environment does not contain the module itself. You should download it additionally in your account and copy it inside the environment as described below.

1. Copy usm_peleng folder from this folder to userside bundle folder
2. Add service setup from docker-compose.yml to bundle docker-composer.yml
3. Download usm_peleng from https://my.userside.eu and unzip two files (usm_peleng.pl and usm_peleng.conf-example) into the usm_peleng/module folder.
4. Rename usm_peleng.conf-example to usm_peleng.conf and setup $usUrl and $usApiKey. Do not modify parameter $logsPath! Setup optional parameters, if needed.
5. Copy usm_peleng.cron to host /etc/cron.d folder and modify as needed and change path to bundle (or standalone) docker-compose.yml
6. Restart userside docker bundle for building the docker-image
```
docker-compose stop
docker-compose up --build -d
```

## Test

To test the module, run it manually.
```
docker-compose run --rm usm_peleng perl usm_peleng.pl
```

## Any questions?

All questions are accepted only through the ticket system of your account.