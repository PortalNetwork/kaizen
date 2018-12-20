
# Install Ethereum

## Installing from PPA

```
sudo apt-get install software-properties-common
sudo add-apt-repository -y ppa:ethereum/ethereum
sudo apt-get update
sudo apt-get install ethereum
```

If you want to stay on the bleeding edge, install the `ethereum-unstable` package instead.

After installing, run `geth account new` to create an account on your node.

You should now be able to run `geth` and connect to the network.

Make sure to check the different options and commands with `geth --help`

You can alternatively install only the `geth` CLI with `apt-get install geth` if you don't want to install the other utilities (`bootnode`, `evm`, `disasm`, `rlpdump`, `ethtest`).


# In order to save the storage cost we using s3 to storage the sync data of Ethereum

## Setup s3



## Step 1：Create s3fs passwd file

```
$ touch /etc/passwd-s3fs
```

## Step 2：Edit s3fs file

```
$ vim /etc/passwd-s3fs
```

## Step 3：Setup S3 bucket with bucket name and IAM user's access key id、secret access key

```
bucketName:accessKeyID:secretAccessKey
```

## Step 4：Auth s3fs 

```
$ chmod 640 /etc/passwd-s3fs
```

## Step5：New S3 bucket direction

```
$ mkdir /mnt/s3-drive
```

## Step6：mount S3 bucket 

```
$ /usr/bin/s3fs <bucket-name> /mnt/s3-drive -o allow_other passwd_file=/etc/passwd-s3fs
```



## Step7: Then start geth with this command to redirct your chaindata location into s3 drive you just setting with

```
 $ geth --rpc --rpcaddr 0.0.0.0 --rpcport 8545 --rpcvhosts=* --datadir "/mnt/s3-drive"
```
