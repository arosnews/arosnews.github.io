---
layout: post
title: How to prepare a USB flash drive
subtitle: with AROS ABIv11
lang: en
tag: tutorial
ref: tutPendrive
---

You can download AROS ABIv11 as an .iso file and prepare a bootable CD from it. But what if we do not have a CD drive in our machine with AROS, or for other reasons we prefer to create a bootable USB flash drive with the system? Nothing simpler - just install AROS on the USB drive in a similar way as if you were installing it on a hard drive. The best way to do this is to use a virtual machine.

## Step 1: Download and install VirtualBox

VirtualBox is a free and open source program for creating and running virtual machines on your computer. To download it, you can visit the [official VirtualBox download site](https://www.virtualbox.org/wiki/Downloads) or [Oracle Technology Network](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html). There you will find links to installation files and code sources for various platforms. I downloaded and installed the Windows version. If you have problems with the installation I refer you to [this tutorial](https://itsfoss.com/install-virtualbox-windows/).

## Step 2: Create a virtual machine running AROS

![Install](/assets/img/64pend2__.png)

Click the **New** button to create a new virtual machine. Point to our downloaded .iso file with AROS ABIv0, select *Other* in the **Type:** field and **Version:** *Other/Unknown (64-bit)* in the Version field.

![Install](/assets/img/64pend3__.png)

Set the memory and number of processors as above.

![Install](/assets/img/64pend4__.png)

If you are only going to use our virtual machine to prepare a flash drive you can choose not to create a virtual disk.

![Install](/assets/img/64pend5__.png)

![Install](/assets/img/64pend6__.png)

Your virtual machine is ready. AROS will boot on this default configuration.

## Step 3: Install AROS on the USB flash drive

![Install](/assets/img/64pend7__.png)

Insert your USB flash drive and select it under **Devices/USB** options.

![Install](/assets/img/64pend8__.png)

Click on the InstallAROS icon. In the installer window, select *Wipe disk*, and in **Drive type:** *USB*. Note that the installer will delete all partitions on this USB drive.

![Install](/assets/img/64pend9__.png)

![Install](/assets/img/64pend10__.png)

After resetting the virtual machine, click InstallAROS again, this time check *Use existing AROS partitions (on any drive)*.

![Install](/assets/img/64pend11__.png)

Here you can additionally check *Install Debugging tools and Developer Software* if you intend to use these tools.

![Install](/assets/img/64pend12__.png)

![Install](/assets/img/64pend13__.png)

![Install](/assets/img/64pend14__.png)

![Install](/assets/img/64pend15__.png)

![Install](/assets/img/64pend16__.png)

After the installer finishes copying the files, press *Proceed* one last time and your USB flash drive with the system is ready. You can now install AROS on real hardware, preferably get a computer from the [recommended list](https://en.wikibooks.org/wiki/Aros/Platforms/x86_Complete_System_HCL#Recommended_hardware_(64-bit)).
