# Vast DB Nifi 2.x using Docker Compose

## Overview

This project configures NiFi 2.x with the latest [Vast DB NiFi Extension](https://github.com/vast-data/vastdb_nifi).

NiFi is deployed with a self generated SSL certificate that is only valid for 60 days.  Currently, the environment will need to be destroyed and re-created when the certificate expires.

This environment is only suitable for dev/test due to the cert expiration issue.
```
┌────────────────────┐     ┌─────────────────────┐   ┌─────────────────────┐             
│                    │     │                     │   │                     │
│  ┌──────────────┐  │     │   ┌─────────────┐   │   │   ┌────────────┐    │
│  │              │  │ 443 │   │             │   │   │   │  Vast DB   │    │ 
│  │     User     ├──┼─────┼──►│ NiFi 2.0.0  ├───┼───┼──►│            │    │ 
│  │              │  │     │   │             │   │   │   │  Vast S3   │    │
│  └──────────────┘  │     │   └─────────────┘   │   │   └────────────┘    │
│                    │     │                     │   │                     │
│     User Host      │     │     Server Host     │   │     Vast Host       │
└────────────────────┘     └─────────────────────┘   └─────────────────────┘
```


## Instructions

```
ssh your_server_host_ip_or_name

git clone https://github.com/snowch/vast_nifi_docker_compose.git
cd vast_nifi_docker_compose

# set this to your server host name
export EXT_HOST=your_server_host_ip_or_name

docker compose up
```

Open the URL https://your_server_host_ip_or_name/nifi

- Username: admin
- Password: 123456123456

## Notes

- Only tested on Linux AMD64 server hosts
- Only deploys a single NiFi node
