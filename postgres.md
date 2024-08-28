# Operations in PostgreSQL

## Author

| Created/Updated | Version    | Author     | Comment         |
|-----------------|------------|------------|-----------------|
| 10-06-2024      | 1          |Kaif Shakeel| Initial Commit  |

## Table of Content

1. [Introduction](#introduction)
2. [Runtime Dependencies](#runtime-dependencies)
3. [Build-time Dependencies](#build-time-dependencies)
4. [System Requirement](#system-requirement)
5. [Important Ports](#important-ports)
6. [Installation](#installation)
7. [Application Build](#application-build)
8. [Running the Application in the Background](#running-the-application-in-the-background)
9. [Contact Information](#contact-information)
10. [References](#references)


## Introduction

This document consists of the pre-built and post-built steps of postgreSQL. If anyone wishes to learn more and take a deep dive into the detailed documentation of PostgreSQL, one can refer to [this](https://github.com/mygurkulam-p9/documentation/blob/main/OT-Microservices/Postgresql/Detailed%20Document/postgresql.md) document.


## Runtime Dependencies

These are the dependencies required for running PostgreSQL once it has been built and installed.

| Dependency | Description |
|------------|-------------|
| **Python** | If Python is used as a procedural language. |
| **Perl** | If Perl is used as a procedural language. |

## Build-time Dependencies


| Dependency | Description |
|------------|-------------|
| **GCC (GNU Compiler Collection)** | The compiler for building the PostgreSQL source code. |
| **Perl** | For some build scripts and regression tests. |
| **Python** | For some build scripts and tools. |


## System Requirement 

The minimum hardware required to install and run PostgreSQL is:

| Component          | Requirement                                                      |
|--------------------|------------------------------------------------------------------|
| CPU/ Instance Type | 1 GHz processor or faster/ t2.micro                              |
| Memory             | 2 GB of RAM                                                      |
| Storage            | 512 MB of available hard drive space/ EBS Storage                |


## Important Ports

| Inbound Traffic | Description |
|-----------------|-------------|
| 5432 | Default Port |


## Installation
### Linux
```sh
sudo apt update
sudo apt install postgresql postgresql-contrib
```

### macOS
```sh
brew update
brew install postgresql
```

### Windows
Download the PostgreSQL installer from the official website and run the setup.

Application Configuration Changes
- Edit `postgresql.conf` for general server configuration.
- Edit `pg_hba.conf` to configure client authentication.

## Application Build
When compiling from source:
```sh
./configure
make
sudo make install
```

## Running the Application in the Background

```sh
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

## Contact Information

| Contact      | Details                             |
|--------------|-------------------------------------|
| Email        | kaif.shakeel.snaatak@mygurukulam.co |

## References

| Reference                         | Details                                                       |
|-----------------------------------|---------------------------------------------------------------|
| High Availability and Monitoring  | https://www.postgresql.org/docs/8.2/high-availability.html    |
