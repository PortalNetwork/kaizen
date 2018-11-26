# Setting up NKN on DigitalOcean

>

https://m.do.co/c/fcbab816fcb1


## What is needed

### SSH Terminal 
- Windows: Recommend Putty, [https://www.putty.org/](https://www.putty.org/)
- Mac OS: Using default terminal

## Getting Started

### Login
If you already have DigitalOcean account, you can login into your account.

### Sign up
If you don't have DigitalOcean account, please sign up.

### 1. Create Droplets
### Droplets configuration
- Choose an image
    - Debian: 9.5 x 64

- Choose a size
    - CPU: 1 GB
    - SSD: 25 GB
    - Transfer: 1000 GB
    - Price: $5 / month

- CPU Optimized Droplets (Skip)
- Add backups (Skip)
- Add block storage (Skip)
- Choose a datacenter region
    - Bangalore

- Select additional options (Skip)
- Add your SSH keys (Skip)
- Finalize and create
    - Choose a hostname: _Type a name you'd like_ or using default

- Click __Create__

### 2. Connect to node
After create the Droplets, you will receive the email include:
- Droplet Name
- IP Address
- Username
- Password

Using terminal/putty to connect the droplet node
```
$ ssh root@<IP_ADDRESS>
```

_NOTE: You must change your password at the first time you connect to the droplet node._

### 3. Installation

Update Debian 
```
apt-get update
```

Use the latest version
```
apt-get upgrade
```

If you are asked what you want to do with it just stick with "keep the local version currently installed"

Install dependencies
```
apt-get install -y make curl git
```

Look up the goland latest version of go and store the download path in "url":
```
url=`curl https://golang.org/dl/ | grep linux-amd64 | sort --version-sort | tail -1 | grep -o -E "https://dl.google.com/go/go[0-9]+\.[0-9]+((\.[0-9]+)?).linux-amd64.tar.gz"`
```

Download the file
```
wget ${url}
```

Unzip the file
```
sudo tar -C /usr/local -xvf `echo ${url} | cut -d '/' -f5`
```

Finally set environment variables correctly: Please enter line by line with pressing RETURN.
```
cat >> ~/.bashrc << 'EOF'
export GOPATH=$HOME/go
export PATH=/usr/local/go/bin:$PATH:$GOPATH/bin
EOF
```

Re-source bash
```
source .bashrc
```

### 4. Download and build

Create folder for NKN
```
mkdir -p ~/go/src/github.com/nknorg && cd ~/go/src/github.com/nknorg
```

Clone the NKN repository
```
git clone https://github.com/nknorg/nkn.git
```

Change directory to NKN source
```
cd nkn
```

Install glide package management
```
make glide
```

Download dependencies for building
```
make vendor
```

Build the source code with make
```
make
```

#### Testnet config and wallet creation
The configuration of a NKN Node is stored in the config.json file. Fortunately NKN already has a testnet configuration file for you which has only to be copied. Just type
```
cp config.testnet.json config.json
```

If you want to create a new wallet for NKN type:
```
./nknc wallet -c
```

#### Test mining
```
./nknd -p YOUR_WALLET_PASSWORD
```

## Reference
- https://medium.com/nknetwork/setting-up-a-nkn-miner-in-5-minutes-and-run-it-free-for-2-months-with-digitalocean-76bafcd82ae8