---
layout: post
title: Odyssey Web Browser w AxRT Linux
subtitle: instrukcja instalacji
lang: pl
ref: tutOWBal
---

Do zainstalowania Odyssey Web Browser pod linuksem użyjemy najnowszej dystrybucji **Linux Mint 22 "Willma" (Cinnamon Edition)**. Upewnij się w **Update Manager**, że system jest w pełni aktualny. 

![hosted1](/assets/img/hosted1.png)

Korzystając z linuksowej przeglądarki ściągnij ze strony [https://axrt.org/download/axrt/4.0/](https://axrt.org/download/axrt/4.0/) najnowsze archiwa z pakietem [**LibAxRT**](https://axrt.org/download/axrt/4.0/packages/libaxrt-4.0_41.12-1_amd64.deb), bibliotekami [**OWB-Libs**](https://axrt.org/download/axrt/4.0/other/OWB-Libs-for-x86_64-axrt.zip), przeglądarką [**OWB**](https://archives.aros-exec.org/share/network/browser/owb-2.1.x86_64-aros-v11.zip) i launcherem dla OWB [**StartOWB**](https://axrt.org/download/axrt/4.0/other/StartOWB).

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

W katalogu owb-x86_64 zmień nazwę pliku “OWB.info.axrt” na “OWB.info”. Dzięki temu będziesz miał ikonę z tooltype uruchamiającym OWB wykorzystujące CONCURRENT_JIT.  

Możesz teraz uruchomić Oddysey Web Browser klikając w **StartOWB**. Pamiętaj, że pierwsze uruchomienie OWB trwa dłużej niż zwykle, gdyż inicjowane są w tym czasie czcionki.

![axrt6](/assets/img/axrt6.png)

{: .box-success}
Pomiędzy aplikacjami AxRT, a systemem hostującym działa schowek. Możesz używać schowka za pomocą CTRL+C, CTRL+V po stronie hosta oraz AMIGA+C, AMIGA+V po stronie AxRT.

Zapraszam na forum [AROS World](https://www.arosworld.org), gdzie możesz zadać dodatkowe pytania na temat użytkowania AROSa, AxRT i OWB. Możesz też tam zgłaszać napotkane błędy w działaniu.

