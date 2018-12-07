# Setting up Wanchain on AWS

> Wanchain aims to build a super financial market of digital assets. It is an infrastructure connecting different digital assets.

## What is needed

### SSH Terminal 
- Windows: Recommend Putty, [https://www.putty.org/](https://www.putty.org/)
- Mac OS: Using default terminal

## Getting Started

### Login
If you already have AWS account, you can login into your account.

### Sign up
If you don't have AWS account, please sign up.

## 1. Create AWS EC2

### AWS EC2 configuration
- Choose an image
    - Ubuntu: 18.04 x 64

![Choose AMI](https://s3.amazonaws.com/kaizen-images/github/aws_choose_ami.png)

- Choose an instance
    - Type: t2.micro (Free tier)
    - vCPUs: 1
    - Memory: 1 GB
    - Storage: EBS only

![Choose Instance](https://s3.amazonaws.com/kaizen-images/github/aws_choose_instance.png)

Review the instance information
![Review Instance](https://s3.amazonaws.com/kaizen-images/github/aws_review_instance.png)

### Using AWS S3 to store Wanchain blockchain data

## 2. Connect to node

```
ssh -i <PEM_PATH> ubuntu@<HOSTNAME>
```

![Launch Instance](https://s3.amazonaws.com/kaizen-images/github/aws_launch_instance.png)

## 3. Download and build

Before begin to setup the envirment we need to update first.
```
sudo apt-get update
```

In order to install brew on Ubuntu we need to install some kit 
```
sudo apt-get install build-essential curl git ruby libbz2-dev \libcurl4-openssl-dev libexpat-dev libncurses-dev zlib1g-devtar xvfz gwan-linux-amd64-1.0.4-b7ce29ea.tar.gz
```

Install rabbitmq (Ubuntu )

```
sudo apt-get install rabbitmq-server
```

Download install brew from source  to mount AWS S3 

```
git clone https://github.com/Homebrew/linuxbrew.git ~/.linuxbrew
```

Install all the kit tbears need
```
brew install automake
```

```
brew install libtool
```

```
apt-get install -y pkg-config
```

```
brew install libtool
```

```
brew install libffi
```

```
brew install gmp
```

tbears is a python library so we need to install python3 and pip3 before we start to install tbears

```
sudo apt install python3
```

```
sudo apt install pip3
```

Now we can use pip3 to intall tbears

```
pip3 install tbears
```



Create and change directory to the ICON source

```
mkdir & cd work
```

Try to start ICON node
```
tbears start
```

tbears will automaticlly init rabbitmq also:
```
ubuntu@ip-172-31-35-214:~/work$ tbears start
[2018-12-07 09:33:26 +0000] [20712] [INFO] Starting gunicorn 19.7.1
[2018-12-07 09:33:26 +0000] [20712] [INFO] Listening at: http://0.0.0.0:9000 (20712)
[2018-12-07 09:33:26 +0000] [20712] [INFO] Using worker: sanic.worker.GunicornWorker
[2018-12-07 09:33:26 +0000] [20728] [INFO] Booting worker with pid: 20728
[2018-12-07 09:33:26 +0000] [20730] [INFO] Booting worker with pid: 20730
[2018-12-07 09:33:26 +0000] [20729] [INFO] Booting worker with pid: 20729
Started tbears service successfully

```



## Notice:

The ndoe we trying to start is private chain, if you want to switch to another net you need to fix the uri section inside tbears_cli_config.json.

Please change the uri with the following net's API endpoint, then start tbears again.

## Testnet for DApps

Please note that current testnet can be reset anytime, and you may experience unexpected downtime. We are working on preparing a more stable final test environment along with less-managed multiple playground networks.

|                  |                                         |
| ---------------- | --------------------------------------- |
| Name             | Yeouido (여의도)                        |
| Node             | https://bicon.net.solidwallet.io        |
| API endpoint     | https://bicon.net.solidwallet.io/api/v3 |
| Network ID (nid) | 3                                       |
| Tracker          | https://bicon.tracker.solidwallet.io    |
| Transaction fee  | on                                      |
| SCORE audit      | off                                     |


## Testnet for Exchanges

Euljiro network is exclusively open to the exchange developers.

|                  |                                        |
| ---------------- | -------------------------------------- |
| Name             | Euljiro (을지로)                       |
| Node             | https://test-ctz.solidwallet.io        |
| API endpoint     | https://test-ctz.solidwallet.io/api/v3 |
| Network ID (nid) | 2                                      |
| Tracker          | https://trackerdev.icon.foundation     |
| Transaction fee  | on                                     |
| SCORE audit      | on                                     |


## Mainnet

|                  |                                   |
| ---------------- | --------------------------------- |
| Name             | ICON Mainnet                      |
| Node             | https://ctz.solidwallet.io        |
| API endpoint     | https://ctz.solidwallet.io/api/v3 |
| Network ID (nid) | 1                                 |
| Tracker          | https://tracker.icon.foundation   |
| Transaction fee  | on                                |
| SCORE audit      | on                                |
