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

## Configuration

Following the official guidance, once a clean install has been performed, copy the `LocalSettings.php` from the docker container
### Configure database usernames and password

The database usernames and passwords aren't stored in this repository,
so you'll have to create the file which contain them yourself. First
create the file `mysql_secrets` with the following, replacing the text
in square brackets with what ever you want:

```
MYSQL_DATABASE=[my_wiki]
MYSQL_USER=[<mysql_username>]
MYSQL_PASSWORD="[<mysql_password>]"
```

Then create the file `mediawiki_secrets` with the following, replacing
the text in square brackets so it matches the contents of
`mysql_secrets`.

```
<?php
$wgDBname = "[my_wiki]";
$wgDBuser = "[<mysql_username>]";
$wgDBpassword = "[<mysql_password>]";
```

The docker compose file will pick up both of these secrets files (mediawiki_secrets as a volume, mysql_secrets as an env_file).

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
