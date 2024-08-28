![Screenshot 2024-06-06 152622](https://github.com/cdivyanshu/Documentation-snaatak/assets/160396963/a1d0bc78-9c9d-4124-9d2d-1e66ff432c31)

# ScyllaDB | Run ScyllaDB locally

|      Created/Updated       | Version | Author      | Comment   |           
|:-----------------:|:----------:|:------------:|:-----------------:|
|04-06-2024| V1 | Divyanshu Chaudhary |Initial Commit|

## Table Of Content

- [Introduction](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#introduction)
- [Pre-requisites](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#pre-requisites)
- [System Requirements](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#system-requirements)
- [Dependencies](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#dependencies)
- [Setup](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#setup)
- [Official Support](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#official-support)
- [Contacts](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#contact)
- [References](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Run%20ScyllaDB%20locally/README.md#references)


## Introduction
This documentation provides an overview of how to set up ScyllaDB locally. ScyllaDB is a high-performance, open-source distributed NoSQL database designed for ultra-low-latency and high-throughput applications. It supports the same protocol as Apache Cassandra, which allows for seamless integration and migration from Cassandra to ScyllaDB. In addition to setup instructions, this documentation also covers monitoring techniques for ScyllaDB, ensuring you can maintain optimal performance and health of your database cluster. Key monitoring commands, such as nodetool status, will be discussed to help you effectively manage and troubleshoot your ScyllaDB deployment.

## Pre-requisites

Before diving into the Installation of scyllaDB, let’s ensure the following pre-requisites meets as its requirements.

## Software Overview
|                  |         |
|:----------------:|:-------:|
| **Software Name:**| ScyllaDB|
|**Version:**| 5.4 |

## System Requirements

| Hardware specifications | Minimum Requirement  |
|:-----------------------:|:--------------------:|
| Operating System        | Ubuntu 22.04         |
| Architecture            | x86_64 or AArch64    |
| Memory                  | 64 GB-256 GB recommended|
| Logical Cores           | 4-8 Logical Cores is recommended|
| Network                 | 10Gbps networking is recommended for high-performance workloads|


## Dependencies

ScyllaDB requires certain dependencies to be installed on your system for both runtime and build purposes. The following table outlines the necessary dependencies and their versions:

### Runtime Dependencies

| Dependency | Version Requirement |
|:----:|:----:|
|JAVA|ScyllaDB requires Java 11 or later.|

## Setup

#### Mentioning two ways to install scyllaDB on our Linux machine:

####  Using script for the installation.
```
curl -sSf get.scylladb.com/server | sudo bash
sudo scylla_io_setup
```
![scylla-1](https://github.com/cdivyanshu/Documentation-snaatak/assets/160396963/d9e2d17b-4322-4edc-8279-7c6f6b29c01b)

![scylla-2](https://github.com/cdivyanshu/Documentation-snaatak/assets/160396963/233d00d4-63ab-49a7-bbb6-4ffedbd72e6d)

##### To start the scylla-server and check status use this command.

```
sudo systemctl start scylla-server
sudo systemctl status scylla-server
```

![scylla-3](https://github.com/cdivyanshu/Documentation-snaatak/assets/160396963/e4c2a82a-6ddb-4f4f-b138-bc17cd831733)

##### To start scylla use this command
```
cqlsh
```

![scylla-4](https://github.com/cdivyanshu/Documentation-snaatak/assets/160396963/8af9303a-9080-4470-b370-fdb10e4846a8)

####  Step-by-step Installation of ScyllaDB on Ubuntu:

##### Step 1: System Preparation:

> Create keyrings directory:
```
sudo mkdir -p /etc/apt/keyrings
```

> Add GPG key:
```
sudo gpg --homedir /tmp --no-default-keyring --keyring /etc/apt/keyrings/scylladb.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys d0a112e067426ab2
```

> Add ScyllaDB repository:
```
sudo wget -O /etc/apt/sources.list.d/scylla.list http://downloads.scylladb.com/deb/debian/scylla-5.4.list
```

> Update package list:
```
sudo apt-get update
```

##### Step 2: Install ScyllaDB and Dependencies

> Install ScyllaDB:
```
sudo apt-get install -y scylla
```

> Install Java Runtime:
```
sudo apt-get install -y openjdk-11-jre-headless
sudo update-java-alternatives --jre-headless -s java-1.11.0-openjdk-amd64
```

> Check for the latest version of ScyllaDB:
```
apt-cache madison scylla
```

> Install ScyllaDB components:
```
sudo apt-get install scylla{,-server,-jmx,-tools,-tools-core,-kernel-conf,-node-exporter,-conf,-python3}=<latest version>
```

##### Step 3: Configuration

> Edit scylla.yaml:
```
sudo vi /etc/scylla/scylla.yaml
```

> Run Scylla setup:
```
sudo scylla_setup --no-raid-setup --online-discard 1 --no-sysconfig-setup --io-setup 0 --no-cpuscaling-setup --no-rsyslog-setup
```

> Setup Scylla I/O:
```
sudo scylla_io_setup
```

##### Step 4: Start ScyllaDB

> Start ScyllaDB service:
```
sudo systemctl start scylla-server
```

> Check the status of the service:
```
sudo systemctl status scylla-server
```
![scylla-3](https://github.com/cdivyanshu/Documentation-snaatak/assets/160396963/e4c2a82a-6ddb-4f4f-b138-bc17cd831733)


## Official Support

|                |                                       |
|:--------------:|:-------------------------------------:|
|[Support](https://www.scylladb.com/product/support/)|Reach out to ScyllaDB support for any issues or questions|
|[Community](https://forum.scylladb.com/)|Join the ScyllaDB community forums for discussions and help from other users|

## Contact

|    NAME           |   Email Address                       |
|:-----------------:|:-------------------------------------:|
|Divyanshu Chaudhary| Divyanshu.chaudhary.snaatak@mygurukulam.co  |


## References

[Documentation](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/ScyllaDB%20%20Detailed%20documentation/README.md)

[ScyllaDB Installation Guide](https://opensource.docs.scylladb.com/stable/getting-started/install-scylla/index.html)
