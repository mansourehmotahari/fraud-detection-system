# fraud-detection-system
## Introduction

[![Kafka](https://img.shields.io/badge/streaming_platform-kafka-black.svg?style=flat-square)](https://kafka.apache.org)
[![Docker Images](https://img.shields.io/badge/docker_images-confluent-orange.svg?style=flat-square)](https://github.com/confluentinc/cp-docker-images)
[![Python](https://img.shields.io/badge/python-3.5+-blue.svg?style=flat-square)](https://www.python.org)

This is a simple fraud detection system with kafka & python.

## How to run
These instructions will get you a copy of the project up and running on your local machine.

* Prerequisites

    Make sure that you have Python 3.x, pip and git installed.

First, You have to clone this repository (or you can download zip file)

```bash
 git clone https://github.com/mansourehmotahari/fraud-detection-system.git
```

You will need [Docker](https://docs.docker.com/install/) and [Docker Compose](https://docs.docker.com/compose/) to run it.Then you need kafka images.

You can install the images as usual with pip: 

```bash
 docker pull confluentinc/cp-kafka
```
And we also need:

```bash
 docker pull confluentinc/cp-zookeeper
```

we'll use an external Docker network called kafka-network to allow both Kafka cluster and the apps to access the same network:

```bash
 docker network create kafka-network
```

Now run the following command to bring your kafka containers up.

```bash
 cd fraud-detection-system
 docker-compose -f docker-compose.kafka.yml up
```
After that, you should be able to start the transaction generator and the fraud detector, in a new cmd window:

```bash
 cd fraud-detection-system
 docker-compose up
```
Finally, you can show streams of transactions in seperate terminals:

valid transactions:

```bash
 cd fraud-detection-system
 docker-compose -f docker-compose.kafka.yml exec broker kafka-console-consumer --bootstrap-server localhost:9092 --topic valid
```
fraud transaction:

```bash
 cd fraud-detection-system
 docker-compose -f docker-compose.kafka.yml exec broker kafka-console-consumer --bootstrap-server localhost:9092 --topic fraud
```



