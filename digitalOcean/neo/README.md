# Setting up NEO on DigitalOcean

> NEO is a non-profit community-driven blockchain project. It utilizes blockchain technology and digital identity to digitize assets and automate the management of digital assets using smart contracts. Using a distributed network, it aims to create a "Smart Economy".

## What is needed

### SSH Terminal

- Windows: Recommend Putty, <https://www.putty.org/>
- Mac OS: Using default terminal

## Getting Started

### Login

If you already have DigitalOcean account, you can login into your account.

### Sign up

If you don't have DigitalOcean account, please sign up.

## 1. Create Project

[![Create Project](https://camo.githubusercontent.com/e671515f25c34e582e35c909a7349d09aeaddf82/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f6372656174655f70726f6a6563742e706e67)](https://camo.githubusercontent.com/e671515f25c34e582e35c909a7349d09aeaddf82/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f6372656174655f70726f6a6563742e706e67)

## 2. Create Droplets

[![Create Droplet](https://camo.githubusercontent.com/97daf57bae21be0adcc994f1c553bb255065cb66/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f6372656174655f64726f706c65742e706e67)](https://camo.githubusercontent.com/97daf57bae21be0adcc994f1c553bb255065cb66/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f6372656174655f64726f706c65742e706e67)

### Droplets configuration

- Choose an image
  - Debian: 9.5 x 64
- Choose a size
  - CPU: 1 GB
  - SSD: 25 GB
  - Transfer: 1000 GB
  - Price: $5 / month

[![Choose Image](https://camo.githubusercontent.com/39cfcdc79996292406879cbcf72a5f83c94ee6aa/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f63686f6f73655f6e6b6e5f696d6167652e706e67)](https://camo.githubusercontent.com/39cfcdc79996292406879cbcf72a5f83c94ee6aa/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f63686f6f73655f6e6b6e5f696d6167652e706e67)

- CPU Optimized Droplets (Skip)
- Add backups (Skip)
- Add block storage (Skip)
- Choose a datacenter region
  - Bangalore

[![Choose Region](https://camo.githubusercontent.com/0d436a7b70190cdab41975630dd917d627b93ea1/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f63686f6f73655f726567696f6e2e706e67)](https://camo.githubusercontent.com/0d436a7b70190cdab41975630dd917d627b93ea1/68747470733a2f2f73332e616d617a6f6e6177732e636f6d2f6b61697a656e2d696d616765732f6769746875622f63686f6f73655f726567696f6e2e706e67)

- Select additional options (Skip)
- Add your SSH keys (Skip)
- Finalize and create
  - Choose a hostname: *Type a name you'd like* or using default
- Click **Create**

## 3. Connect to node

After create the Droplets, you will receive the email include:

- Droplet Name
- IP Address
- Username
- Password

Using terminal/putty to connect the droplet node

```
$ ssh root@<IP_ADDRESS>
```

*NOTE: You must change your password at the first time you connect to the droplet node.*

## 4. Installation

Update Debian

```
apt-get update
```

Install Database

```
sudo apt-get install unzip libleveldb-dev sqlite3 libsqlite3-dev libunwind8-dev
```

We are using neo-python to setup everything so we need to install python3 and pip3 first

Install python3

```
apt install python3 
```

Install pip3

```
apt install pip3
```



## 5. Download and build

Create folder for NEO

```
git clone https://github.com/CityOfZion/neo-python.git
```

Change directory to NEO source

```
cd neo-python
```

Before we can install neo-python there are two libirary need to be installed first

Openssl 

```
apt-get install openssl
```

 Libssl

```
apt-get install libssl-dev
```

Install neo-python

```
pip3 install neo-python
```

To speed up the syn process:

Bootstrap the testnet blockchain

```
np-bootstrap
```

Bootstrap the testnet notifications database 

```
np-bootstrap -n
```



### Start testnet and wallet creation

Its easy to start NEO testnet now, just typing the following cmd 

```
np-prompt
```

If you want to create a new wallet for NEO:

```
create wallet {your_wallet_name} 
```

Open  wallet

```
open wallet {your_wallet_name}
```

