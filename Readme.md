# Docker Compose file showing how to install plugins in the official MediaWiki image

## Installation

### Install Docker

Install Docker according to the [official
instruction](https://docs.docker.com/install/linux/docker-ce/debian/#install-using-the-repository).

### Dockerfile

The file `mediawiki/Dockerfile` adds the plugins I use to the [official
MediaWiki docker image](https://hub.docker.com/_/mediawiki/).

- This can be modified with additional extensions for mediawiki as necessary
- Rebuild the image and push to your chosen docker repository
- Reference the same image in the docker compose file

### Docker Compose

Two compose files are provided - one that supports `armv7` architecture, and the other that supports `amd64`

My main use case is to deploy on a Raspberry Pi 4, so the armv7 support is required.

## Configuration

Following the official guidance, once a clean install has been performed, copy the `LocalSettings.php` from the docker container

### Configure database usernames and password

The docker compose file uses `environment` variables to specify connection credentials for the db. When running the GUI MediaWiki setup for the first time, it's important that the provided credentials for the DB are the same as the ones in the docker compose file. IT IS STRONGLY RECOMMENDED THAT YOU CHANGE THESE BEFORE STARTING THE INSTALL.

```
MYSQL_DATABASE=[my_wiki]
MYSQL_USER=[<mysql_username>]
MYSQL_PASSWORD="[<mysql_password>]"
```

### Extension:Scribunto

This comes pre-installed with MW 1.34 and above (so no need to add to docker file)

- [Scribunto Extension](https://www.mediawiki.org/wiki/Extension:Scribunto): 
  - Configuration steps for extension

### Extension:VisualEditor

This comes pre-installed with MW 1.34 and above (so no need to add to docker file)

- [VisualEditor Extension](https://www.mediawiki.org/wiki/Extension:VisualEditor): 
  - Configuration steps for visual editor
- [MediaWiki-Docker VisualEditor](https://www.mediawiki.org/wiki/MediaWiki-Docker/Extension/VisualEditor) 
  - Development docker environment configuration

### Extension:TemplateData

This comes pre-installed with MW 1.35 and above (so no need to add to docker file)

- [TemplateData Extension](https://www.mediawiki.org/wiki/Extension:TemplateData): 
  - Configuration steps for extension

### Extension:BetaFeatures

- [BetaFeatures Extension](https://www.mediawiki.org/wiki/Extension:VisualEditor): 
  - Configuration steps for visual editor
- [MediaWiki-Docker VisualEditor](https://www.mediawiki.org/wiki/MediaWiki-Docker/Extension/VisualEditor) 
  - Development docker environment configuration

### Skin:Citizen

This is the skin installed with the custom docker image

- [Citizen Skin](https://www.mediawiki.org/wiki/Skin:Citizen) 
  - Configuration steps for the skin
