# Vast DB Nifi 2.x Single Node using Docker Compose

## Overview

NiFi 2.0.0-M4 can be time consuming to setup due to its SSL requirements.

This project configures NiFi 2.x with a traefik reverse proxy using docker compose to quickly try NiFi 2.x with the latest [Vast DB NiFi Extension](https://github.com/vast-data/vastdb_nifi).

NiFi is deployed with a self generated SSL certificate that is only valid for 60 days.  Currently, the environment will need to be destroyed and re-created to overcome that.

NiFi 2.0.0-M5 fixes a [bug](https://issues.apache.org/jira/browse/NIFI-13680) that will allow NiFi to be run on `http` which will hopefully remove the need for this project.

```
                           ┌───────────────────────────────────────────┐
                           │                                           │
                           │                                           │
┌──────────────┐           │   ┌─────────────┐       ┌─────────────┐   │
│              │    443    │   │ Traefik     │       │             │   │
│  User        ├───────────┼──►│ Reverse     ├──────►│ NiFi 2.0.0  │   │
│              │           │   │ Proxy       │       │             │   │
└──────────────┘           │   └─────────────┘       └───────┬─────┘   │
                           │                                 │         │
                           │         Host: docker compose    │         │
                           └─────────────────────────────────┼─────────┘
                                                             │          
                                                             ▼          
                                                      ┌────────────┐    
                                                      │  Vast DB   │    
                                                      │            │    
                                                      │  Vast S3   │    
                                                      └────────────┘    
```


## Instructions

```
ssh your_host

git clone https://github.com/snowch/vast_nifi_docker_compose.git
cd vast_nifi_docker_compose

docker compose up
```

Open the URL https://your_host/nifi

- Username: admin
- Password: 123456123456

## TODO

- Only tested on Linux AMD64 server hosts
