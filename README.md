# DAppBoard Documentation
How to install, run and hack [DAppBoard](http://dappboard.com).

Table of content:
  * [1. Introduction](#1-introduction)
  * [2. Installation](#2-installation)
    + [A. Prerequisite](#a-prerequisite)
    + [B. Setup](#b-setup)
      - [a. Common tools](#a-common-tools)
      - [b. ETL and Database](#b-etl-and-database)
      - [c. Web](#c-web)
  * [2. Running](#2-running)
    + [A. ETL](#a-etl)
    + [B. Web](#b-web)
  * [3. License and attribution](#3-license-and-attribution)

## 1. Introduction

The DAppBoard project is a suite of open source tools used to capture and analyze Ethereum blockchain data. It is separated into 4 repositories:
* [ETL](https://github.com/DAppBoard/dappboard-etl): The tools that are extracting and transforming the blockchain data to our database.
* [Web](https://github.com/DAppBoard/dappboard-web): A backend and frontend based on SailsJS. This is what you see when you visit [dappboard.com](http://dappboard.com).
* [Environment](https://github.com/DAppBoard/dappboard-environment): Contains script and environment variable you will nedd to run DAppBoard ETL and Web.
* [Documentation](https://github.com/DAppBoard/dappboard-documentation): What you are reading now, how to setup and run your own DAppBoard.

## 2. Installation

### A. Prerequisite

Running DAppBoard requires few resources

* **Ubuntu 18.04 server**: any other distribution should work but this is what we use.
* **PostgreSQL database**: or any compatible system like Amazon Aurora.

We are currently hosting our pipeline at [DigitalOcean](http://digitalocean.com) and would like to thanks them for their support.


### B. Setup

#### a. Common tools

On a fresh Ubuntu server clone the environment installation script and run it as an administrator. It will install all the tools needed to run the ETL and Web interface.

``cd ~ && git clone https://github.com/DAppBoard/dappboard-environment.git && cd dappboard-environment && sudo ./install_server.sh``

You will then need to fill the environment file, the sample one is available here ```dappboard-evnvironment/env_sample``` and you'll need to fill the following informations:

```
# Database connection informations
export DAPPBOARD_PSQL_HOST=""
export DAPPBOARD_PSQL_DB=""
export DAPPBOARD_PSQL_USER=""
export DAPPBOARD_PSQL_PASSWORD=""

# The connection string for your RPC node or Infura
export DAPPBOARD_NODE_URL=""

# Only necessary for scripts that are fetching data from Etherscan (ABI/Sourcecode)
export DAPPBOARD_ETHERSCAN_API=""
```

Once you filled the information, source it and add it to your general environment.

```source env_sample && sudo cat env_sample >> /etc/environment```

#### b. ETL and Database

For installing the ETL, we just need to clone the repo and install NPM dependencies.

``cd ~ && cd dappboard-etl/etl && npm install``

You will then need to create all the tables and indexes. For this connect to your PostgreSQL database and run the SQL queries located in the ```dappboard-etl/schemas/tables/``` folder or [here](https://github.com/DAppBoard/dappboard-etl/tree/master/schemas/tables).

#### c. Web

Installing the web part is optionnal as it's only valuable if you want to replicate DAppBoard. We publish it for learning and transparency purpose.

 ``cd ~ && cd dappboard-web/ && npm install``

## 2. Running

### A. ETL

We use PM2 in order to run and monitor node script: it was installed with the server environment. In the home folder run:

```pm2 start etl.ecosystem.config.js```

This will start all the ETL scripts:
* **live** is responsible for getting new blocks and ingesting them.
* **past** is responsible for going back in time for ingesting the blocks.
* **scrape_tokens** is running every hour and get information about the tokens that emitted Transfer events.

### B. Web

In the web folder, run:

```sails lift```

## 3. License and attribution

Everything you see (sources, documentation) is published under the MIT License.

We invite you to use our work and contribute. If you use our tools or some of our data: feel free to tell it to the world!
