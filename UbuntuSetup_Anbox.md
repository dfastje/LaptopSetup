What I did to get it working on Ubuntu 18.4.3 

### Installing Andbox
```
sudo apt update
sudo apt upgrade
snap install --devmode --beta anbox
```
This installed anbox, but it would crash on startup. 

### Troubleshooting Andbox
Found several bug docs on similar issues, but this is the 
  one that solved my problem (https://github.com/anbox/anbox/issues/364). 
  Note that I toggled back and forth between the beta and edge branches. 

```
sudo add-apt-repository ppa:morphis/anbox-support
sudo apt update
sudo apt install anbox-modules-dkms
sudo modprobe ashmem_linux
sudo modprobe binder_linux

sudo snap refresh --devmode --beta anbox
```
If you run into secure boot issues, I found these help pages while troubleshooting: (https://github.com/anbox/anbox/issues/1070), (https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1566221)

### Installing playstore

To get the playstore, I found a really nice script (https://github.com/geeks-r-us/anbox-playstore-installer/) 
  and tutorial (https://www.linuxuprising.com/2018/07/anbox-how-to-install-google-play-store.html) that handles this process:
  
```
sudo apt install wget lzip unzip squashfs-tools

wget https://raw.githubusercontent.com/geeks-r-us/anbox-playstore-installer/master/install-playstore.sh
chmod +x install-playstore.sh

sudo ./install-playstore.sh

sudo ./install-playstore.sh --clean

anbox.appmgr
```

Next, go into Anbox's settings app to enable the permissions of both of these apps: "Google Play Services" and "Google Play Store." After that step, I was able to successfully log into one of my google accounts and download all of the needed apps that do not have a desktop equivalent!
