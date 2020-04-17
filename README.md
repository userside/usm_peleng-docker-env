# USM_PELENG Docker Environment

This environment provides the feature of running the usm_peleng module inside the Docker container. This environment does not contain the module itself. You should download it additionally in your account and copy it inside the environment as described below.

1. Copy usm_peleng folder from this folder to userside bundle folder
2. Add service setup from docker-compose.yml to bundle docker-composer.yml
3. Download usm_peleng from https://my.userside.eu and unzip two files (usm_peleng.pl and usm_peleng.conf-example) into the usm_peleng/module folder.
4. Rename usm_peleng.conf-example to usm_peleng.conf and setup parameters: `$usUrl = "http://nginx";` and `$usApiKey`. **Do not** modify parameter `$logsPath`! Setup other optional parameters, if needed.
5. Copy usm_peleng.cron to host folder `/etc/cron.d` and change path to bundle (or your standalone) docker-compose.yml
6. Build docker-image for service usm_peleng
```
docker-compose build
```

## Test

To test the module, run it manually.
```
docker-compose run --rm usm_peleng perl usm_peleng.pl
```

## Any questions?

All questions are accepted only through the ticket system of your account.