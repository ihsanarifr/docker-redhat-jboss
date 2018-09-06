# Docker Red Hat JBoss Product

Docker running Red Hat Jboos Product.

## Overview

1. [Install prerequisites](#install-prerequisites)

    Before installing project make sure the following prerequisites have been met.

2. [Clone the project](#clone-the-project)

    We’ll download the code from its repository on GitHub.

3. [Run the application](#run-the-application)

    By this point we’ll have all the project pieces in place.
___

## Install prerequisites

For now, this project has been mainly created for Unix `(Linux/MacOS)`. Perhaps it could work on Windows.

All requisites should be available for your distribution. The most important are :

* [Git](https://git-scm.com/downloads)
* [Docker](https://docs.docker.com/engine/installation/)
* [Docker Compose](https://docs.docker.com/compose/install/)

Check if `docker-compose` is already installed by entering the following command : 

```sh
which docker-compose
```

Check Docker Compose compatibility :

* [Compose file version 2 reference](https://docs.docker.com/compose/compose-file/)

The following is optional but makes life more enjoyable :

```sh
which make
```

On Ubuntu and Debian these are available in the meta-package build-essential. On other distributions, you may need to install the GNU C++ compiler separately.

```sh
sudo apt install build-essential
```

### Images to use
* [JbossJDK:8](https://hub.docker.com/r/jboss/base-jdk/)
* Download [Red Hat Jboss Enterprise Application Platform (EAP) lastest version](https://developers.redhat.com/products/eap/download/?referrer=jbd)
* Download [Red Hat Jboss Fuse lastest version](https://developers.redhat.com/products/fuse/download/)
This project use the following ports :

| Server               |  Port  |
|----------------------|--------|
| Jboss EAP Management |  10190 |
| Jboss EAP Service    |  8280  |
___

## Clone the project

To install [Git](http://git-scm.com/book/en/v2/Getting-Started-Installing-Git), download it and install following the instructions :

```sh
git clone https://github.com/ihsanarifr/docker-redhat-jboss.git
```

Go to the project directory :

```sh
cd docker-redhat-jboss
```

### Project tree

```sh
.
├── README.md
├── jboss-eap-7.1
│    ├── source
│    │    └── jboss-eap-{JBOSS_VERSION}.zip (you must download)
│    └── Dockerfile
├── wildfly
│    └── Dockerfile
├── .env.example
└── docker-compose.yml
```

___

## Run the application

1. Open your favorite browser for Jboss EAP Management:
    * [http://localhost:10190/](http://localhost:10190/)
2. For Wildfly
    * [http://localhost:9990/](http://localhost:9990/)
___

## Help us

Any thought, feedback or (hopefully not!)