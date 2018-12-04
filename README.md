# DAppBoard Documentation
How to install, run and hack [DAppBoard](http://dappboard.com).

## 1. Installation

### A. Introduction

The DAppBoard project is a suite of open source tools used to capture and analyze Ethereum blockchain data. It is separated into 4 repositories:
* [ETL](https://github.com/DAppBoard/dappboard-etl): The tools that are extracting and transforming the blockchain data to our database.
* [Web](https://github.com/DAppBoard/dappboard-web): A backend and frontend based on SailsJS. This is what you see when you visit [dappboard.com](http://dappboard.com).
* [Environment](https://github.com/DAppBoard/dappboard-environment): Contains script and environment variable you will nedd to run DAppBoard ETL and Web.
* [Documentation](https://github.com/DAppBoard/dappboard-documentation): What you are reading now, how to setup and run your own DAppBoard.

### B. Prerequisite

Running DAppBoard requires few resources

* **Ubuntu 18.04 server**: any other distribution should work but this is what we use.
* **PostgreSQL database**: or any compatible system like Amazon Aurora.

We are currently hosting our pipeline at [DigitalOcean](http://digitalocean.com) and would like to thanks them for their support.


### C. Setup

#### a. Common tools

On a fresh Ubuntu server clone the environment installation script and run it as an administrator. It will install all the tools needed to run the ETL and Web interface.

``cd ~ && git clone https://github.com/DAppBoard/dappboard-environment.git && cd dappboard-environment && sudo ./install_server.sh``

#### b. ETL and Database

For installing the ETL, we just need to clone the repo and install NPM dependencies.

``cd ~ && git clone https://github.com/DAppBoard/dappboard-etl.git && cd dappboard-etl/etl && npm install``

You will then need to create all the tables and indexes. For this connect to your PostgreSQL database and run the SQL queries located in the ```dappboard-etl/schemas/tables/``` folder or [here](https://github.com/DAppBoard/dappboard-etl/tree/master/schemas/tables).

#### c. Web

Installing the web part is optionnal as it's only valuable if you want to replicate DAppBoard. We publish it for learning and transparency purpose.

 ``cd ~ && git clone https://github.com/DAppBoard/dappboard-web.git && cd dappboard-web/ && npm install``

### D. Running



## License and attribution

Everything you see (sources, documentation) is published under the MIT License.

We invite you to use our work and contribute. If you use our tools or some of our data: feel free to tell it to the world!
