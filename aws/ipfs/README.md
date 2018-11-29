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

![Launch Instance](https://s3.amazonaws.com/kaizen-images/github/aws_launch_ipfs_instance.png)

## 3. Download and build

Download newest version from IPFS
```shell
wget https://dist.ipfs.io/go-ipfs/v0.4.18/go-ipfs_v0.4.18_linux-386.tar.gz
```

Unzip the file
```shell
tar xvfz go-ipfs_v0.4.18_linux-386.tar.gz
```

Run the script to install IPFS
```shell
cd go-ipfs
sudo ./install.sh
```

## 4. Start service

Initilize IPFS
```shell
ipfs init
```

Start IPFS daemon
```shell
ipfs daemon
```

Done! The IPFS daemon is started.

## 5. Upload file to IPFS

```shell
echo "hello world" | ipfs add
added QmT78zSuBmuS4z925WZfrqQ1qHaJ56DQaTfyMUF7F8ff5o QmT78zSuBmuS4z925WZfrqQ1qHaJ56DQaTfyMUF7F8ff5o
```

Try it out: https://gateway.ipfs.io/ipfs/QmT78zSuBmuS4z925WZfrqQ1qHaJ56DQaTfyMUF7F8ff5o
