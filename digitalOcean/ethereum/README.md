# Setting up Ethereum on DigitalOcean

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


### 4. Download and build
