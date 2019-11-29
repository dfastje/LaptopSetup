What I did to get it working on Ubuntu 18.4.3 

```
sudo apt update
sudo apt upgrade
snap install --devmode --beta anbox
```
This installed anbox, but it would crash on startup. Found several bug docs on similar issues; but this is the 
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
