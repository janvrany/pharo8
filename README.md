# Pharo 8

This repository contains a *fork* of Pharo 8 used for ST25 development.

## Bootstrapping Pharo from sources

The bootstrapping can be done on a properly-named branch using the following script:

```
BUILD_NUMBER=42 BOOTSTRAP_ARCH=32 bash ./bootstrap/scripts/bootstrap.sh
```

This will generate and archive images at various stages of the bootstrap process up to the full image in Pharo8.0-32bit-hhhhhhh.zip where hhhhhhh is the hash of the current checkout.

Additional information on the stages of the bootstrap and how to snapshot during the process are provided as comments in bootstrap.sh.

__Tip:__ You can set `BOOTSTRAP_REPOSITORY` and `BOOTSTRAP_CACHE` environment variables to do the bootstrap outside of the source repository.

__Note:__ If you are on a branch that doesn't follow the expected naming convention ('`PharoX.Y`'), then the script will pick an appropriate default (such as `Pharo7.0`). To build Pharo8.0 from a custom branch, you need to set `BRANCH_NAME=Pharo8.0` before the bootstrap script is run. 

## Setting up build host

### Ubuntu 18

```
sudo dpkg --add-architecture i386 && sudo apt update
sudo apt install zlib1g:i386 libssh2-1:i386 libssl1.0.0:i386
```

### Ubuntu 22

```
sudo dpkg --add-architecture i386 && sudo apt update
sudo apt install zlib1g:i386 libssh2-1:i386
(wget http://security.ubuntu.com/ubuntu/pool/main/o/openssl1.0/libssl1.0.0_1.0.2n-1ubuntu5.13_i386.deb \
	&& rm -rf /tmp/openssl && mkdir /tmp/openssl \
	&& dpkg -x libssl1.0.0_1.0.2n-1ubuntu5.13_i386.deb /tmp/openssl \
	&& sudo cp -arv /tmp/openssl/usr /)
```

## How to contribute

Pharo is an opensource project very friendly to contributions of the users. See the document [CONTRIBUTING](CONTRIBUTING.md) how you can help to improve Pharo.



