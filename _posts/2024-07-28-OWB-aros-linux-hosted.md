---
layout: post
title: Odyssey Web Browser on AROS Linux hosted
subtitle: installation manual
tag: tutorial
lang: en
ref: tutOWBh
---

We will use the latest **Linux Mint 22 “Willma” (Cinnamon Edition)** distribution to install **AROS** as hosted by Linux. Make sure in **Update Manager** that the system is fully up to date.

![hosted1](/assets/img/hosted1.png)

Run **Software Manager** and install the **Uml-utilities** package.

![hosted2](/assets/img/hosted2.png)

Using a Linux browser, download the latest archives with **AROS** and **OWB**   
[https://www.axrt.org/download/aros/v11/AROS-20241102-1-linux-x86_64-system.tar.bz2](https://www.axrt.org/download/aros/v11/AROS-20241102-1-linux-x86_64-system.tar.bz2)  
[https://archives.aros-exec.org/share/network/browser/owb-2.1.x86_64-aros-v11.zip](https://archives.aros-exec.org/share/network/browser/owb-2.1.x86_64-aros-v11.zip)  

Extract the AROS directory from the archive to /home/username/ (where *"username ”* is your username in your Linux home directory).

![hosted5](/assets/img/hosted5.png)

Extract the archive with OWB to any place in the AROS directory structure. I extracted to *AROS/Extras/Networking/Apps/* and renamed the directory from **owb-x86_64** to **OWB**.

![hosted6](/assets/img/hosted6.png)

Copy to *AROS/boot/linux/* the **startaros.sh** file, which contains the network script on the Linux side and starts AROS.

{: .box-note}
Download file:  
[startaros.sh](/assets/startaros.sh "download")

![hosted7](/assets/img/hosted7.png)

Open the file in a text editor and rename the network interfaces to those on your system.

![hosted8](/assets/img/hosted8.png)

To check the names of your network interfaces, run **Advanced Network Configuration**.

![hosted9](/assets/img/hosted9.png)

Select the name of the network connection and click on the settings icon. In the *Device* field is the name of the network interface. In my case, the wifi card is named **wlp2s0**, and the ethernet card is named **eno1**. In your case, these names may be different. Remember to enter them correctly in the script.

![hosted10](/assets/img/hosted10.png)

Right-click on the properties of the **startaros.sh** file and in the *Permissions* tab check the box *Allow executing file as program*.

![hosted11](/assets/img/hosted11.png)

Add an AROS launcher icon to your desktop. Right-click on the desktop and select *Create a new launcher here...* In the **Command** field, type */home/AROS/username/boot/linux/startaros.sh* (remember to change the username in this path to your own). Check the “Launch in terminal” box and press “OK”.

![hosted12](/assets/img/hosted12.png)

The configuration on the Linux side ends there. After booting the system from the icon, AROS will open in a new window as shown in the following screen shot. You will customize the appearance of the system in the AROS preferences. 

Screen resolution: *System/Prefs/ScreenMode*.  
Font size: *System/Prefs/Font*.  
Size of other fonts and other settings: *System/Prefs/Zune*.  

![hosted13](/assets/img/hosted13.png)

The network settings on the AROS side are important. Set them in *System/Prefs/Network* exactly as shown in the following screenshot:

![networkhosted](/assets/img/network.png)

Test your internet connection. Run *System/System/Shell* and run the **ping** command, such as “ping google.com”. 

![ping](/assets/img/ping.png)

If you have configured everything correctly and the Internet is working, you can now launch Odyssey Web Browser. Note that the first startup of OWB takes longer than usual, as fonts are downloaded during this time.

![hosted14](/assets/img/hosted14.png)

You can now enjoy OWB on your modern hardware. Feel free to visit the **[AROS World](https://arosworld.org)** forum, where you can ask additional questions about using AROS and OWB. You can also report there any performance bugs you encounter.

![hosted15](/assets/img/hosted15.png)

