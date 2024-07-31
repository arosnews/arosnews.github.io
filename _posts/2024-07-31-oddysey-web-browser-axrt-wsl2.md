---
layout: post
title: Oddysey Web Browser w AxRT Windows 11 (WSL2)
subtitle: instrukcja instalacji
lang: pl
ref: tutOWBaw
---

W tym krótkim tutorialu pokażę jak uruchomić Oddysey Web Browser na komputerze z Windows 11 z zainstalowanym WSL2. Jedną z prostszych metod na zainstalowanie WSL2 jest skorzystanie z **WSL Manager**. Możesz go pobrać ze Sklepu Microsoft lub bezpośrednio ze [strony Github projektu](https://github.com/bostrot/wsl2-distro-manager/releases).

Przy pierwszym uruchomieniu, jeśli nie miałeś wcześniej systemie WSL, **WSL Manager** przeprowadzi cię przez proces instalacji (wymagany będzie restart komputera). Po ponownym uruchomieniu przejdź do ustawień i zaznacz opcję **GuiAplications** na **true**.

![axrtWSL1](/assets/img/axrtWSL1.png)

Dodaj nową instancję WSL. Na poniższym screenie widzisz, że ja nazwałem swoją instancję *ubuntu*, wybrałem instalację *Ubuntu 24.04* i wpisałem swoją nazwę użytkownika, którą będę się posługiwał w linuksowym podsystemie.

![axrtWSL2](/assets/img/axrtWSL2.png)

Korzystając z windowsowej przeglądarki ściągnij ze strony [https://axrt.org/development/owb/x86_64/](https://axrt.org/development/owb/x86_64/) najnowsze archiwa z pakietem **LibAxRT**, bibliotekami **OWB-Libs**, przeglądarką **OWB** i launcherem dla OWB **StartOWB**.

![axrtWSL3](/assets/img/axrtWSL3.png)

Skopiuj pakiet **LibAxRT** oraz plik **StartOWB** do katalogu domowego użytkownika podsystemu WSL. Masz dostęp do katalogów WSL z poziomu Exploratora Plików Windows.

![axrtWSL4](/assets/img/axrtWSL4.png)

Uruchom terminal z Ubuntu. 

![axrtWSL5](/assets/img/axrtWSL5.png)

Korzystając z terminala, wykonaj kolejno komendy:
- rozpakuj pakiet **LibAxRT**
```
sudo dpkg -i ~/libaxrt-4.0_41.10-1_amd64.deb
```
- ustaw uprawnienia dla pliku **StartOWB**
```
chmod +x StartOWB
```
- uruchom plik **StartOWB**
```
./StartOWB
```
  
![axrtWSL6](/assets/img/axrtWSL6.png)

Po uruchomieniu **StartOWB** w katalogu domowym użytkownika WSL zostaną utworzone katalogi *SYS* oraz *Work*. 

{: .box-note}
Uruchomienie dowolnej aplikacji AxRT spowoduje utworzenie w katalogu domowym katalogów *SYS* oraz *Work*.

![axrtWSL7](/assets/img/axrtWSL7.png)

Rozpakuj wcześniej pobrane archiwa **OWB-Libs** i **OWB** do utworzonych katalogów.  

- Archiwum z **OWB-Libs** do */home/username/SYS*  

![axrtWSL8](/assets/img/axrtWSL8.png)
   
- Archiwum z **OWB** do */home/username/Work*

![axrtWSL9](/assets/img/axrtWSL9.png)

- Przenieś plik **StartOWB** do katalogu z Oddysey Web Browser (*/home/username/Work/owb-x86_64*).

![axrtWSL10](/assets/img/axrtWSL10.png)

Możesz teraz uruchomić Oddysey Web Browser z poziomu terminala. Przejdź do katalogu z OWB i uruchom plik StartOWB.  
```
cd Work/owb-x86_64  
./StartOWB
```

Możesz też utworzyć skrót na pulpicie. Pamiętaj, aby w ścieżce wpisać swoją własną nazwę użytkownika.

```
"C:\Program Files\WSL\wslg.exe" -- "/home/username/Work/owb-x86_64/StartOWB"
```

![axrtWSL12](/assets/img/axrtWSL12.png)

Zapraszam na forum [AROS World](https://www.arosworld.org), gdzie możesz zadać dodatkowe pytania na temat użytkowania AROSa, AxRT i OWB. Możesz też tam zgłaszać napotkane błędy w działaniu.
  
![axrtWSL11](/assets/img/axrtWSL11.png)
