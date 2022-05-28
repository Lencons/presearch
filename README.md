# Presearch

Presearch is a decentralized search engine to which you can find more information about it at https://presearch.io/

The objective of this project is to provide Docker Compose start-up scripts to complement the official Docker directions provided at https://docs.presearch.org/nodes/setup.


## Run Instructions

Instructions are only provided for Linux systems and I am assuming that you already have Docker and Docker Compose installed and running.

1. Copy the ```docker-compose.yml``` file within this repository into your working directory.
1. Create a ```docker-compose.override.yml``` as described below and update it with your Presearch registeration code.
1. The containers can be started with ```docker-compose up -d```
1. Monitor the startup of the node with ```docker logs -f presearch-node```, when then node is running a "Node is listening for searches..." log entry will be seen.
1. Once the node is responding to requests, stats will appear in your dashboard at https://nodes.presearch.com/dashboard

# Docker Compose Sensitive Information

Sensitive information such as the registration code has been removed from the ```docker-compose.yml``` file and a ```docker-compose.override.yml``` is used to inject the required environment variables into the container at run time. Using the template below create a ```docker-compose.override.yml``` file in the working directory.

```yml
version: '3'

services:
  presearch-node:
    environment:
      - REGISTRATION_CODE="registration-code"
      - DESCRIPTION="node-desc"
      - URL="your-url"
      - STAKE="your-stake"
```
Only the REGISTRATION_CODE value is required for the node to start, the other values can be removed from the file and updated later via https://nodes.presearch.com/dashboard.

