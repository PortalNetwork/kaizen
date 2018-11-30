# Start a Ontology on DigitalOcean

> Ontology is a new high-performance public blockchain project & a distributed trust collaboration platform. Ontology provides new high-performance public blockchains that include a series of complete distributed ledgers and smart contract systems.

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
  - Ubuntu 18.04
- Choose a size
  - CPU: 1 GB
  - SSD: 25 GB
  - Transfer: 1000 GB
  - Price: $5 / month

![Choose Image](https://s3.amazonaws.com/kaizen-images/github/choose_ipfs_image.png)

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

Update Ubuntu 

```
apt-get update
```



## 5. Download and build

Get the necessary kit and installed

```
curl https://dev.ont.io/ontology_install | sh
```

Change directory to Ontology source

```
cd ontio
```

Get all Ontology CLI command

```
./ontology --help
```

### Start testnet and wallet creation

Before you can start a node on Digital Ocean, you need to open up a wallet ( account )

```
./ontology account add -d
```

Check your wallet address 

```
./ontology account list
```

Now you can start a node ( testnet )

```
./ontology --networkid 2
```

