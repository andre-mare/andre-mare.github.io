---
layout: post
title: "Install Apache Kafka on macOS using Homebrew"
author: andre
categories: [ kafka ]
tags: [homebrew, macOS, kafka]
image: /assets/images/feature-images/feature-image-kafka.jpg
description: This post provides a step-by-step guide with a list of commands on how to install Apache Kafka on macOS using Homebrew.
comments: true
---

- Table of Contents
{:toc .large-only}

Apache Kafka is a popular open-source stream-processing software platform developed by the Apache Software Foundation. 
Installing and configuring Kafka can sometimes be daunting, but the process is significantly simplified thanks to 
Homebrew (or brew), a package manager for macOS.

This blog will guide you through installing Kafka on macOS using Homebrew. 

## What is Kafka?
> "Apache Kafka acts as a decoupling layer between source and target systems, allowing source systems to produce data into Kafka, and target systems to consume data from Kafka, making the architecture more scalable and manageable." [Apache Kafka][1]


## Brew Installation Commands
Before installing Kafka using Homebrew, you must ensure that Homebrew is installed on your Mac. Once Homebrew is 
installed, you can use the `brew install` command to install both Kafka and Zookeeper, as Kafka has a dependency on 
Zookeeper which will be resolved by Homebrew automatically.

*Command: Install Homebrew*
```shell
$ /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
 ```

*Command: Install Kafka*
```shell
$ brew install kafka
```
This command will install both Kafka and Zookeeper, as Zookeeper is a dependency for Kafka.


## Directory Structure 
After the installation is complete, the Kafka and Zookeeper binaries, configurations, and logs will be located in 
different directories based on your Mac's chip.

**Macs with Intel Processor:**
* Binaries and scripts will be in `/usr/local/bin`
* Kafka configurations will be in `/usr/local/etc/kafka`
* Zookeeper configuration will be in `/usr/local/etc/zookeeper`
* The `log.dirs` config (Kafka data) will be set to `/usr/local/var/lib/kafka-logs`

**Macs with Apple Silicon Processor:**
* Binaries and scripts will be in `opt/homebrew/bin`
* Kafka configurations will be in `opt/homebrew/etc/kafka`
* Zookeeper configuration will be in `opt/homebrew/etc/zookeeper`
* The `log.dirs` config (Kafka data) will be set to `opt/homebrew/var/lib/kafka-logs`

You can modify the Kafka and Zookeeper configuration files to customize your setup.

## Brew Run Commands
Once you have installed Kafka and Zookeeper, you can start them using the brew services command. This command will start 
Kafka and Zookeeper as background services, so they will continue running even if you close your terminal.

*Command: Start Zookeeper and Kafka*
```shell
$ brew services start zookeeper
$ brew services start kafka
```

*Command: Stop Zookeeper and Kafka*
```shell
$ brew services stop kafka
$ brew services stop zookeeper
```

*Command: Restart Zookeeper and Kafka*
```shell
$ brew services restart kafka
$ brew services restart zookeeper
```

## Alternative Commands
While Homebrew provides a convenient way to manage services, you can also start Zookeeper and Kafka manually using the 
provided scripts. This involves running the `zookeeper-server-start.sh` and `kafka-server-start.sh` scripts with the 
appropriate configuration files.

*Command: Start Zookeeper*
```shell
$ /usr/local/bin/zookeeper-server-start /usr/local/etc/zookeeper/zoo.cfg
```

*Command: Start Kafka*
```shell
$ /usr/local/bin/kafka-server-start /usr/local/etc/kafka/server.properties
```

Closing the terminal window or using the `Ctrl-C` command will stop the Kafka and Zookeeper services. It is 
important to stop the services properly to avoid any data corruption or loss.

## Testing Installation
Testing the Kafka installation involves starting the environment, creating a topic, producing events, and consuming 
events. After successfully performing these tasks, it is important to clean up the environment by deleting the created 
topic and stopping the Kafka and Zookeeper services to ensure that the system is left in a clean state.

*Command: Start Zookeeper and Kafka*
```shell
$ brew services start zookeeper
$ brew services start kafka
```


Creating a topic in Kafka can be done using the `kafka-topics -- create` command. After creating the topic, it is important to 
validate its creation by describing the topic using the command `kafka-topics --describe`, which will display the details 
of the created topic.

*Command: Create a Topic*
```shell
$ kafka-topics --create --topic quickstart-events --bootstrap-server localhost:9092
$ kafka-topics --describe --topic quickstart-events --bootstrap-server localhost:9092
```

Producing new events in Kafka can be done using the `kafka-console-producer` command. This will send a `Hello World` event
to the Kafka topic you created.

*Command: Produce Events*
```shell
$ kafka-console-producer.sh --topic quickstart-events --bootstrap-server localhost:9092
> Hello World 1.
> Hello World 2.
```
You can stop the producer client with `Ctrl-C` at any time.

Consuming the events in Kafka can be done using the `kafka-console-consumer` command. This will retrieve the `Hello World` event
from the Kafka topic you created.

*Command: Consume Events*
```shell
$ kafka-console-consumer --topic quickstart-events --from-beginning --bootstrap-server localhost:9092
> Hello World 1.
> Hello World 2.
```
You can stop the consumer client with `Ctrl-C` at any time.


Cleaning up the environment after testing the Kafka installation involves several steps. First, you need to delete the 
topic you created using the `kafka-topics` command, then you need to shut down Kafka and Zookeeper using the 
`brew services stop` commands, and finally, you need to delete any data of your local Kafka environment, including any 
events you have created along the way, by removing the Kafka logs and Zookeeper data directories that were specified 
in the configuration files.

*Command: Environment Cleanup*
```shell
$ kafka-topics --delete --topic quickstart-events --bootstrap-server localhost:9092
$ brew services stop kafka
$ brew services stop zookeeper
$ rm -rf /tmp/kafka-logs /tmp/zookeeper /tmp/kraft-combined-logs
```

## Summary
Installing Kafka on macOS is straightforward using Homebrew. With just a few commands, you can have Kafka and Zookeeper 
up and running on your machine. 

Happy streaming!

[1]:https://kafka.apache.org/
