# Python-Django-Docker

lightweight django docker containers using alpine for main web container.

## Installation

1) Running a web container from alpine image to initialize a project.

```
docker run -ti --rm -v /pathToRepo/web/:/data/web alpine:latest sh
```

--rm flag will remove anychanges after exiting the container <a href="https://docs.docker.com/engine/reference/commandline/run/#options">docker run</a> doc.

*pathToRepo/web is like /home/user_name/repo_name/web/ or equivalent.

2) After entering the web image shell (sh) change directory to (/data/web).

```
cd /data/web
```

3) Start fetching and downloading system packages.

```
apk add --update python3 python3-dev postgresql-client postgresql-dev build-base bash gettext vim
```

4) After Downloading and installing sys package use pip3 to install python packages.

```
pip3 install --upgrade pip
pip3 install -r requirements.txt
django-admin startproject yourProjectName
mkdir yourProjectName/static
```

5) Exit the docker image.

```
exit
```

6) In the repo dicrectory run docker-compose, docker-compose will use the .yaml file to build containers, wait and let it do the magic.

```
docker-compose build
```

7) Bring the containers up.

```
docker-compose up
```
or running as background process without logs
```
docker-compose up -d
```

8) Hiding to localhost in your browser to test the django welcome msg.
