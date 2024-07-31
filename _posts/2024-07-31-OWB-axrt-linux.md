---
layout: post
title: Oddysey Web Browser on AxRT Linux
subtitle: installation manual
tag: tutorial
lang: en
ref: tutOWBal
---

To install Oddysey Web Browser under Linux, we will use the latest distribution **Linux Mint 22 “Willma” (Cinnamon Edition)**. Make sure in **Update Manager** that your system is fully up to date. 

![hosted1](/assets/img/hosted1.png)

Using a Linux browser, download the latest archives with the **LibAxRT** package, the **OWB-Libs** libraries, the **OWB** browser and the launcher for OWB **StartOWB** from [https://axrt.org/development/owb/x86_64/](https://axrt.org/development/owb/x86_64/).

![axrt1](/assets/img/axrt1.png)

Install the **LibAxRT** package first.

![axrt2](/assets/img/axrt2.png)

Go into the properties of the **StartOWB** file and under the *Permissions* tab, check the box *Allow executing file as program*. Then run the **StartOWB** file.

![axrt3](/assets/img/axrt3.png)

After running **StartOWB**, *SYS* and *Work* directories will be created in the home directory. 

{: .box-note}
Running any AxRT application will create *SYS* and *Work* directories in the home directory.

![axrt4](/assets/img/axrt4.png)

- Extract the archive with **OWB-Libs** to */home/username/SYS*. 
- Extract the archive with **OWB** to */home/username/Work*.
- Move the **StartOWB** file to the directory with Oddysey Web Browser (*/home/username/Work/OWB-x86_64*).

![axrt5](/assets/img/axrt5.png)

You can now start Oddysey Web Browser by clicking on **StartOWB**. Note that the first startup of OWB takes longer than usual, as fonts are initialized during this time.

![axrt6](/assets/img/axrt6.png)

Feel free to visit the [AROS World](https://www.arosworld.org) forum, where you can ask additional questions about using AROS, AxRT and OWB. You can also report there any performance bugs you encounter.

