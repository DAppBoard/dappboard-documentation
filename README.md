# DAppBoard Documentation
How to install, run and hack [DAppBoard](http://dappboard.com).

## Prerequisite

Running DAppBoard requires few resources

* Ubuntu 18.04 server: any other distribution should work but this is what we use.
* PostgreSQL database: or any compatible system like Amazon Aurora.

We are currently hosting our pipeline at [DigitalOcean](http://digitalocean.com) and would like to thanks them for their support.

## Introduction

The DAppBoard project is separated into 4 repositories:
* [ETL](https://github.com/DAppBoard/dappboard-etl): The tools that are extracting and transforming the blockchain data to our database.
* [Web](https://github.com/DAppBoard/dappboard-web): A backend and frontend based on SailsJS. This is what you see when you visit [dappboard.com](http://dappboard.com).
* [environment](https://github.com/DAppBoard/dappboard-environment): Contains script and environment variable you will nedd to run DAppBoard ETL and Web.
* [Documentation](https://github.com/DAppBoard/dappboard-documentation): What you are reading now, how to setup and run your own DAppBoard.
