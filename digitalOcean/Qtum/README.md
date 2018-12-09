# Start a Qtum node on DigitalOcean

> A decentralized and open-source smart contracts platform and value transfer protocol.Qtum uses proof-of-stake consensus, meaning node operators are rewarded for validating transactions.A DGP governed blockchain where community participants can vote to change certain network parameters.

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
Install Docker

```
apt  install docker.io
```



## 5. Download and build

Pull Qtum latest Image

```
docker pull hayeah/qtumportal:latest
```

### Start  a Qtum node



```
docker run -it --rm \
--name myapp \
-e "QTUM_NETWORK=testnet" \
-v `pwd`:/dapp \
-p 9899:9899 \
-p 9888:9888 \
-p 3889:3889 \
-p 13888:13888 \
hayeah/qtumportal
```




