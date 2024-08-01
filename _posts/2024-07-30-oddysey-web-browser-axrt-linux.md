---
layout: post
title: Odyssey Web Browser w AxRT Linux
subtitle: instrukcja instalacji
lang: pl
ref: tutOWBal
---

Do zainstalowania Odyssey Web Browser pod linuksem użyjemy najnowszej dystrybucji **Linux Mint 22 "Willma" (Cinnamon Edition)**. Upewnij się w **Update Manager**, że system jest w pełni aktualny. 

![hosted1](/assets/img/hosted1.png)

Korzystając z linuksowej przeglądarki ściągnij ze strony [https://axrt.org/development/owb/x86_64/](https://axrt.org/development/owb/x86_64/) najnowsze archiwa z pakietem **LibAxRT**, bibliotekami **OWB-Libs**, przeglądarką **OWB** i launcherem dla OWB **StartOWB**.

![axrt1](/assets/img/axrt1.png)

W pierwszej kolejności zainstaluj pakiet **LibAxRT**.

![axrt2](/assets/img/axrt2.png)

Wejdź we właściwości pliku **StartOWB** i w zakładce *Permissions* zaznacz pole *Allow executing file as program*. Następnie uruchom plik **StartOWB**.

![axrt3](/assets/img/axrt3.png)

Po uruchomieniu **StartOWB** w katalogu domowym zostaną utworzone katalogi *SYS* oraz *Work*. 

{: .box-note}
Uruchomienie dowolnej aplikacji AxRT spowoduje utworzenie w katalogu domowym katalogów *SYS* oraz *Work*.

![axrt4](/assets/img/axrt4.png)

- Rozpakuj archiwum z **OWB-Libs** do */home/username/SYS* 
- Rozpakuj archiwum z **OWB** do */home/username/Work*.
- Przenieś plik **StartOWB** do katalogu z Oddysey Web Browser (*/home/username/Work/owb-x86_64*).

![axrt5](/assets/img/axrt5.png)

Możesz teraz uruchomić Oddysey Web Browser klikając w **StartOWB**. Pamiętaj, że pierwsze uruchomienie OWB trwa dłużej niż zwykle, gdyż inicjowane są w tym czasie czcionki.

![axrt6](/assets/img/axrt6.png)

Zapraszam na forum [AROS World](https://www.arosworld.org), gdzie możesz zadać dodatkowe pytania na temat użytkowania AROSa, AxRT i OWB. Możesz też tam zgłaszać napotkane błędy w działaniu.

