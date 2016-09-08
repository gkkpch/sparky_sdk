# sparky_sdk

Sparky SBC SDK Guide:
To prepare SPARKY image build setup follow the steps of Sparky Ubuntu building environment steps, Then download SDK files from sparky website or sparkysbc git hub.
1 . Sparky Ubuntu building environment.
1.1 Download Ubuntu image 
Download Ubuntu image from http://www.ubuntu.com/download/server/ ubuntu-12.04.4-server-amd64.iso，you have to use 64bit and 12.04LTS version
1.2 Update packages 
$sudo apt-get update
1.3 Install 32bit compatible packages 
$sudo apt-get install ia32-libs
2. Setting build setup
2.1 Setting shell 
Setting shell to bash. 
a) delete older link 
rm –rf /bin/sh 
b) setting new link 
ln -s bash /bin/sh
c) testing 
$ ls -l /bin/sh 
OK:
2.2 Install JDK 
a) sudo apt-get install openjdk-7-jdk 

b) Verify your jdk is installing succesfully or not. 

$ java –version
2.3 Install Packages 
sudo apt-get install git gnupg flex bison gperf build-essential \ 
zip curl libc6-dev libncurses5 libncurses5-dev x11proto-core-dev \ 
libx11-dev:i386 libreadline6-dev:i386 libgl1-mesa-glx:i386 \ 
libgl1-mesa-dev g++-multilib mingw32 tofrodos \ 
python-markdown libxml2-utils xsltproc zlib1g-dev:i386 
sudo ln -s /usr/lib/i386-linux-gnu/mesa/libGL.so.1 /usr/lib/i386-linux-gnu/libGL.so
2.4 Install other tools 
apt-get install vim zip unzip lrzip 
apt-get install wine // generating windows compatible files
3. Sparkysbc SDK
Download SDK components from sparky website/github and copy to /opt/
3.1 List the sdk components :
root@ubuntu:/opt/sparkysbc_sdk/ls
autobuild.sh  kernel  owl  TERMS_OF_USE.TXT  toolchain  u-boot  ubuntu
3.2 Information about SDK components :
 Kernel: contains kernel source with board specific drivers.
Toolchain: This folder contains the arm cross compilation toolchain “arm-linux-gnueabihf”
Owl: board selection and configuration settings , final build Images and  kernel .obj files will be available on owl/out/ folder. 
u-boot: board specific packages.
Ubuntu: root file system
3.3 build image steps
root@ubuntu:/opt/sparkysbc_sdk/ ./autobuild.sh
Select board type:
     1. sparky_emmc
     2. sparky_sd

Which would you like? [sparky_emmc] 2
s500 ubuntu sparky_sd configured.
..
On successful build owl/out/board_os/images folder contains final images.
Example:
root@ubuntu:/opt/sparkysbc_sdk# cd owl/out/sparky_sd_ubuntu/images



