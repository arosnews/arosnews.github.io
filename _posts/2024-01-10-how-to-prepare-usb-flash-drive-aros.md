---
layout: post
title: How to prepare a USB flash drive
subtitle: with AROS ABIv0
lang: en
ref: tutPendrive
---

You can download AROS ABIv0 as an .iso file and prepare a bootable CD from it. But what if we do not have a CD drive in our machine with AROS, or for other reasons we prefer to create a bootable USB flash drive with the system? Nothing simpler - just install AROS on the USB drive in a similar way as if you were installing it on a hard drive. The best way to do this is to use a virtual machine.

## Step 1: Download and install VirtualBox

VirtualBox is a free and open source program for creating and running virtual machines on your computer. To download it, you can visit the [official VirtualBox download site](https://www.virtualbox.org/wiki/Downloads) or [Oracle Technology Network](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html). There you will find links to installation files and code sources for various platforms. I downloaded and installed the Windows version. If you have problems with the installation I refer you to [this tutorial](https://itsfoss.com/install-virtualbox-windows/).

## Step 2: Create a virtual machine running AROS

![Install](/assets/img/pend2__.jpg)

Click the **New** button to create a new virtual machine. Point to our downloaded .iso file with AROS ABIv0, select *Other* in the **Type:** field and **Version:** *Other/Unknown* in the Version field.

![Install](/assets/img/pend3__.jpg)

Set the memory and number of processors as above.

![Install](/assets/img/pend4__.jpg)

If you are only going to use our virtual machine to prepare a flash drive you can choose not to create a virtual disk.

![Install](/assets/img/pend5__.jpg)

![Install](/assets/img/pend6__.jpg)

Your virtual machine is ready. AROS will boot on this default configuration.

## Step 3: Install AROS on the USB flash drive

![Install](/assets/img/pend7__.jpg)

Insert your USB flash drive and select it under **Devices/USB** options.

![Install](/assets/img/pend8__.jpg)

Click on the InstallAROS icon. In the installer window, select *Wipe disk*, and in **Drive type:** *USB*. Note that the installer will delete all partitions on this USB drive.

![Install](/assets/img/pend9__.jpg)

![Install](/assets/img/pend10__.jpg)

After resetting the virtual machine, click InstallAROS again, this time check *Use existing AROS partitions (on any drive)*.

![Install](/assets/img/pend11__.jpg)

Here you can additionally check *Install Debugging tools and Developer Software* if you intend to use these tools.

![Install](/assets/img/pend12__.jpg)

![Install](/assets/img/pend13__.jpg)

![Install](/assets/img/pend14__.jpg)

![Install](/assets/img/pend15__.jpg)

![Install](/assets/img/pend16__.jpg)

After the installer finishes copying the files, press *Proceed* one last time and your USB flash drive with the system is ready. You can now install AROS on real hardware, preferably get a computer from the [recommended list](https://en.wikibooks.org/wiki/Aros/Platforms/x86_Complete_System_HCL#Recommended_hardware).
