---
layout: post
title: How to cross-compile for AROS
subtitle: on Windows 10 / 11 with WSL2
lang: en
ref: tutWSLcross
---

Cross-compiling is the process of developing software on one system that is intended to run on another system. You can compile software for AROS using an AROS port hosted on Linux. Under Windows, this is possible using WSL2 (Windows Subsystem for Linux 2).

## Requirements

To install WSL2 you need:
- Windows 10 May 2020 (2004) or newer operating system
- Computer supporting Hyper-V Virtualization
- Installed driver for vGPU 

{: .box-note}
To run GUI applications on Linux, you must first install the driver below that matches your system. This will allow you to use a virtual graphics processor (vGPU), which enables you to use hardware-accelerated OpenGL rendering.  
[Intel GPU Driver](https://www.intel.com/content/www/us/en/download/19344/intel-graphics-windows-dch-drivers.html)  
[AMD GPU Driver](https://www.amd.com/en/support)  
[NVIDIA GPU Driver](https://www.nvidia.com/Download/index.aspx?lang=en-us)  
  
## WSL2 installation

Open *Command Prompt* with administrator privileges and type:
```
wsl --install -d ubuntu-22.04
```
After completion, restart the computer. Log in to Windows, and the command prompt will open again. This time you will be guided through the Ubuntu configuration using a username and password (they do not have to be the same as the Windows username and password).

Now you can run the *Ubuntu* application from the Start menu to get started, or install the *Microsoft Terminal* application.

To update the packages in your freshly installed Ubuntu, type the command:
```
sudo apt update && sudo apt upgrade
```

{: .box-note}
From the Windows side, you have easy access to the Ubuntu file system by typing in File Explorer **\\\wsl$\Ubuntu-22.04**

## Installing AROS WSL2 hosted x86_64

Install all the required packages. You can do this with one command:
```
sudo apt install git gcc g++ make gawk bison flex bzip2 netpbm autoconf automake libx11-dev libxext-dev libc6-dev liblzo2-dev libxxf86vm-dev libpng-dev gcc-multilib libsdl1.2-dev byacc python3-mako libxcursor-dev cmake genisoimage dh-make unzip
```
For the purposes of this installation, create a directory *myprojects* in your user directory in Ubuntu, and in it a directory *arosbuilds*. Then clone the AROS repository from **deadwood**’s github and copy the *rebuild.sh* file from the AROS directory to the *arosbuilds* directory. Below is a sequence of commands to do this:

```
mkdir myprojects
cd myprojects
mkdir arosbuilds
cd arosbuilds
git clone https://github.com/deadwood2/AROS.git AROS
cp ./AROS/scripts/rebuild.sh .
```
Run the *rebuild.sh* script:
```
./rebuild.sh
```
Select *toolchain-core-x86_64*
```
1) toolchain-core-x86_64
```
When finished, run the *rebuild.sh* script again, this time select *core-linux-x86_64 (DEBUG)*.
```
2) core-linux-x86_64 (DEBUG)
```

{: .box-note}
A network connection is required during compilation, as additional sources are downloaded from the network.

Once the operation is complete, AROS is already installed. You can run it by executing the *AROSBootstrap* file.
```
cd core-linux-x86_64-d/bin/linux-x86_64/AROS
./boot/linux/AROSBootstrap
```

{: .box-note}
If you want to run AROS with a certain amount of memory use the *-m* parameter, e.g., **"-m 1024"** for 1GB RAM

![AROS hosted](/assets/img/aroshosted.jpg)
*AROS x86_64 on WSL2*

On the Ubuntu side, you can use a script that will configure the network connection for AROS. You can create a **startaros.sh** script in your home directory that will set up the network and then start AROS with 1GB of RAM:

```
#!/bin/sh

NETON=`ifconfig | grep aros0`

if [ "$NETON" = "" ]; then
    echo "Installing bridge network... (sudo access required)"
    sudo tunctl -b -u "$USER" -t aros0
    sudo ifconfig aros0 192.168.166.1
    sudo iptables -t nat -A POSTROUTING -o eth0 -s 192.168.166.0/2 -j MASQUERADE
    sudo iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.166.0/2 -j MASQUERADE
    sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
fi

cd myprojects/arosbuilds/core-linux-x86_64-d/bin/linux-x86_64/AROS
./boot/linux/AROSBootstrap -m 1024
```

{: .box-note}
If your network interface has a name other than **eth0**, remember to change it in the script.

So that you can execute the script, change the attributes of the created file:
```
chmod 755 startaros.sh
```

The above script also requires installing additional packages to work:
```
sudo apt install net-tools uml-utilities
```

On the AROS side, in *Prefs/Network*, select the **tap.device** interface and manually set the IP addresses as in the following screenshot:

![Network configuration](/assets/img/networkhosted.jpg)
*Network configuration in AROS WSL2 hosted*

The next step will be to compile the **contrib** so that you have the entire AROS SDK at your disposal.

```
git clone https://github.com/deadwood2/contrib.git contrib
cd contrib
git checkout master
```

Move the downloaded contrib directory to the AROS directory (so that you have *AROS/contrib*). Then go to the *core-linux-x86_64-d* directory and run:
```
make contrib
```

{: .box-note}
If you have a multi-core processor, you can use the **make** command with the *-j* parameter (e.g. **"make -j4 contrib "**) to slightly speed up the build process using more threads.

Create the *cross-x86_64-aros* directory at the same level as the *AROS* and *core-linux-x86_64-d* directories.
```
mkdir cross-x86_64-aros
```
Then create a file in it named x86_64-aros-gcc with the following content:
```
exec /home/username/myprojects/arosbuilds/toolchain-core-x86_64/x86_64-aros-gcc --sysroot=/home/username/myprojects/arosbuilds/core-linux-x86_64-d/bin/linux-x86_64/AROS/Development "$@"
```
And set attributes for it:
```
chmod 755 x86_64-aros-gcc
```

The last step will be to add the cross-x86_64-aros directory to the PATH. To do this permanently open the **.bashrc** file that is in your user home directory and at the very end add the line:

```
export PATH=$PATH:/home/username/myprojects/arosbuilds/cross-x86_64-aros
```

{: .box-note}
Remember to change *username* in the paths to your username.

If all went well, by typing **x86_64-aros-gcc** you should have a working compiler.
```
x86_64-aros-gcc -c hello.c -o hello
```
