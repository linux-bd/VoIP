### Asterisk Installation in Ubuntu Linux System
```sh
sudo su

apt-get update && apt-get upgrade -y && reboot

sudo apt-get install build-essential wget libssl-dev libncurses5-dev libnewt-dev  libxml2-dev linux-headers-$(uname -r) libsqlite3-dev uu
id-dev

cd /usr/src/

wget http://downloads.asterisk.org/pub/telephony/dahdi-linux-complete/dahdi-linux-complete-current.tar.gz

wget http://downloads.asterisk.org/pub/telephony/libpri/libpri-current.tar.gz

wget http://downloads.asterisk.org/pub/telephony/asterisk/asterisk-14-current.tar.gz

tar zxvf dahdi-linux-complete*
tar zxvf libpri*
tar zxvf asterisk*

cd /usr/src/dahdi-linux-complete*
make && make install && make config

cd /usr/src/libpri*
make && make install

cd /usr/src/asterisk*
./configure && make menuselect && make && make install && make config && make samples

[Start DAHDI]
/etc/init.d/dahdi start

[Start Asterisk and connect to the CLI]
/etc/init.d/asterisk start
asterisk -rvvv

[Verify your installation by checking for the DAHDI and libpri versions on the Asterisk CLI]

*CLI> dahdi show version
DAHDI Version: 2.6.1 Echo Canceller: HWEC
*CLI> pri show version
libpri version: 1.4.13
```
