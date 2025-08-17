---
layout: post
title: How to change System language
subtitle: in AROS ABIv11 64-bit
lang: en
tag: tutorial
ref: tutL
---

{: .box-success}
I’ll walk you through the process using the example of the Polish language. The procedure is similar for other languages. Just make sure to select the appropriate character encoding for your language and use fonts that include diacritics relevant to your chosen language.

## Step 1: FTManager and Font Installation

**FreeType Font Manager** allows us to install TrueType fonts in the system with the correct character encoding. For the Polish language, we’ll use *ISO-8859-2*, as that’s the character encoding used by the Polish localization. With ABIv11 64-bit, we receive a set of TrueType fonts located in *AROS:Fonts/TrueType/*.

![TrueType](/assets/img/lang3.jpg)

Not all of these fonts include Polish diacritics. The only ones that do are: Barlow, Bellefair, Carbon, GoodTimes, Pakenham, Spectral, and WorkSans. Not every font will work well as a system font. In reality, we should consider choosing between Barlow or WorkSans.

A good idea is to find an appropriate TrueType font online or use a font from Windows if you’re a Windows user. Just make sure it includes diacritics for your language. Personally, I decided to use the Segoe UI Variable font from Windows 11. To do this, I transferred the SegUIVar.ttf file from *C:/Windows/Fonts/* to *AROS:Fonts/TrueType/* using a USB drive.

![SegUIVar](/assets/img/lang4.jpg)

Now let’s proceed to *AROS:System/FTManager*.

In the **Codepage** field, select *ISO-8859-2* for the Polish language. Next, search for the font name you want to install with the chosen character encoding (in our case, Segoe UI Variable) and double-click its name.

![Codepage](/assets/img/lang5.jpg)

After opening the new window with font parameters, in the **Name** field, you can change the font name as it will appear in the system (for example, you can add “PL” at the end of the name to emphasize that it’s a font with Polish characters). Finally, click *“Install”*. Although nothing seems to happen immediately, after this operation, two new files with the name of our font and the extensions .font and .otag will appear in the *AROS:Fonts/* directory. At this point, the font is installed in the system. You can close the window and proceed to the next step.

![Install](/assets/img/lang6.jpg)


{: .box-success}
If you need **bitmap** fonts, it's best to download a ready-made package from Aminet. For Polish fonts, you can download this file:  
[http://aminet.net/text/bfont/CzcionkiISO.lha](http://aminet.net/text/bfont/CzcionkiISO.lha)  
It contains a set of four typefaces of Polish bitmap fonts in the ISO-8859-2 encoding standard. The contents should be extracted to the *AROS:Fonts/* directory.

## Step 2: Input and Locale

Navigate to *AROS:Prefs/Input*, where we’ll change the keyboard mapping to one suitable for our language. In the **Keyboards** list, double-click on *“Polski”*. The Polish flag will appear in the **Default** field. Click the button located next to it labeled *“Set”* to confirm your choice. Finally, click *“Save”*.

![Input](/assets/img/lang1.jpg)

Next, go to *AROS:Prefs/Locale*. In the **Region** section, select *“Polska”*, and in **Preferred Language**, choose *“Polski”*. For the **Default character set**, select *ISO-8859-2*, as this is the character encoding used by the Polish localization in ABIv11 64-bit. If everything is set as shown in the screenshot below, click *“Save”*.

![Locale](/assets/img/lang2.jpg)

## Step 3: Configuring Fonts in the System

If you have installed one or more fonts with Polish characters, proceed to *AROS:Prefs/Fonts* and select them. You have the option to set different fonts and/or sizes. Click *“Save”* and then navigate to *AROS:Prefs/Zune*. Here, you can adjust fonts in the **“Windows”** and **“Groups”** tabs. After saving the changes, restart your computer, and your basic language switch is complete.

![Fonts](/assets/img/lang7.jpg)

![FontsPref](/assets/img/lang8.jpg)

![ZunePref](/assets/img/lang9.jpg)
