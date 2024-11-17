---
layout: post
title: Odyssey Web Browser on AxRT Windows 11 (WSL2)
subtitle: installation manual
tag: tutorial
lang: en
ref: tutOWBaw
---

In this short tutorial, I will show you how to run Odyssey Web Browser on a Windows 11 computer with WSL2 installed. One of the simpler methods to install WSL2 is to use **WSL Manager**. You can download it directly from [the project's Github page](https://github.com/bostrot/wsl2-distro-manager/releases/tag/v1.8.14). In this tutorial, I used WSL Manager version 1.8.14. 

{: .box-note}
Many motherboards have the virtualization option disabled by default. This option is usually found in the BIOS under advanced processor settings. Turn it on before you proceed with the installation.

The first time you run it, if you have not had a WSL system before, **WSL Manager** will guide you through the installation process (a reboot will be required). After restarting, go to settings and mark **GuiAplications** to **true**.

![axrtWSL1](/assets/img/axrtWSL1.png)

Add a new WSL instance. In the screenshot below you can see that I named my instance *ubuntu*, selected the *Ubuntu 24.04* installation and entered my username, which I will use in the Linux subsystem.

![axrtWSL2](/assets/img/axrtWSL2.png)

Using a windows browser, download the latest archives with the [**LibAxRT**](https://axrt.org/download/axrt/4.0/packages/libaxrt-4.0_41.12-1_amd64.deb) package, the [**OWB-Libs**](https://axrt.org/download/axrt/4.0/other/OWB-Libs-for-x86_64-axrt.zip) libraries, the [**OWB**](https://archives.aros-exec.org/share/network/browser/owb-2.1.x86_64-aros-v11.zip) browser and the launcher for OWB [**StartOWB**](https://axrt.org/download/axrt/4.0/other/StartOWB) from [https://axrt.org/download/axrt/4.0/](https://axrt.org/download/axrt/4.0/).

![axrtWSL3](/assets/img/axrtWSL3.png)

Copy the **LibAxRT** package and **StartOWB** file to the WSL subsystem user's home directory. You have access to the WSL directories from the Windows File Explorer. The *ubuntu* directory is located on the left side of the File Explorer window, under disk names. 

![axrtWSL4](/assets/img/axrtWSL4.png)

Start the terminal with Ubuntu. 

![axrtWSL5](/assets/img/axrtWSL5.png)

Using a terminal, execute the commands in sequence:
- unpack the **LibAxRT** package.
```
sudo dpkg -i ~/libaxrt-4.0_41.10-1_amd64.deb
```
- set permissions for **StartOWB** file.
```
chmod +x StartOWB
```
- run **StartOWB** file
```
./StartOWB
```
  
![axrtWSL6](/assets/img/axrtWSL6.png)

After running **StartOWB**, the *SYS* and *Work* directories will be created in the WSL user's home directory. 

{: .box-note}
Running any AxRT application will create *SYS* and *Work* directories in the home directory.

![axrtWSL7](/assets/img/axrtWSL7.png)

Extract the previously downloaded **OWB-Libs** and **OWB** archives to the created directories.  

- Archive with **OWB-Libs** to */home/username/SYS*  

![axrtWSL8](/assets/img/axrtWSL8.png)
   
- Archive with **OWB** to */home/username/Work*  

![axrtWSL9](/assets/img/axrtWSL9.png)

- Move the **StartOWB** file to the directory with Oddysey Web Browser (*/home/username/Work/owb-x86_64*).

![axrtWSL10](/assets/img/axrtWSL10.png)

You can now run Odyssey Web Browser from a terminal. Navigate to the directory with OWB and run the StartOWB file.  
```
cd Work/owb-x86_64  
./StartOWB
```

You can also create a shortcut on the desktop. Remember to put your own username in the path.

```
"C:\Program Files\WSL\wslg.exe" -- "/home/username/Work/owb-x86_64/StartOWB"
```

![axrtWSL12](/assets/img/axrtWSL12.png)

{: .box-success}
There is a clipboard between the AxRT applications and the hosting system. You can use the clipboard with CTRL+C, CTRL+V on the host side and AMIGA+C, AMIGA+V on the AxRT side.

Feel free to visit the [AROS World](https://www.arosworld.org) forum, where you can ask additional questions about using AROS, AxRT and OWB. You can also report there any performance bugs you encounter.
  
![axrtWSL11](/assets/img/axrtWSL11.png)

## Problems with sound?

You may not have sound, for example, when playing YouTube videos. This is because WSLg in its current version supports PulseAudio, but not ALSA. There is a plug-in called libasound2 (ALSA library) that transfers the call from ALSA to PulseAudio. The plug-in is called pulse. So you need to install the plug-in by running the command in the terminal:
```
sudo apt install libasound2-plugins
```
and enable it manually by creating a **.asoundrc** file in your home directory with the following contents:
```
pcm.default pulse
ctl.default pulse
```
Finally, restart the WSL system.  

{: .box-note}
Download the prepared archive with **.asoundrc** file and extract it in your home directory:  
[.asoundrc](/assets/asoundrc.zip "download")
