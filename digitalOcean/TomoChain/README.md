# Start a Tomochain masternode on DigitalOcean

> Tomochain is a public EVM (Ethereum Virtual Machine)-compatible blockchain with the following advantages: low transaction fee, fast confirmation time, double validation and randomization for security guarantees. In particular, we propose Proof-of-Stake Voting (PoSV) consensus, a Proof-of-Stake (PoS)-based blockchain protocol with a fair voting mechanism, rigorous security guarantees and fast finality. We also present a novel reward mechanism and show that, with this mechanism, the blockchain has a low probability of forks, fast confirmation times, plus the contributions and benefits of masternodes are fair in the sense that the probability distribution function is uniform eventually.

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

![Create Project](https://s3.amazonaws.com/kaizen-images/github/create_project.png)

## 2. Create Droplets

![Create Droplet](https://s3.amazonaws.com/kaizen-images/github/create_droplet.png)

### Droplets configuration

- Choose an image
  - Ubuntu 18.04 x 64
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

![Choose Region](https://s3.amazonaws.com/kaizen-images/github/choose_region.png)

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
Install Python3

```
apt install python3
```

Install Pip3

```
apt install python3-pip
```

Install tmn ( Tomochain python kit )

```
 pip3 install tmn
```


## 5. Download and build

Get the necessary docker kit

```
curl -sSL https://get.docker.com/ | sh
```

Set up docker compose

```
sudo curl -L https://github.com/docker/compose/releases/download/1.18.0/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
```



### Start  a testnet masternode



```
tmn start --name johnnyh --net testnet  --pkey "private key"
```


