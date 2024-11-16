---
layout: post
title: Odyssey Web Browser w AxRT Windows 11 (WSL2)
subtitle: instrukcja instalacji
lang: pl
ref: tutOWBaw
---

W tym krótkim tutorialu pokażę jak uruchomić Odyssey Web Browser na komputerze z Windows 11 z zainstalowanym WSL2. Jedną z prostszych metod na zainstalowanie WSL2 jest skorzystanie z **WSL Manager**. Możesz go pobrać ze Sklepu Microsoft lub bezpośrednio ze [strony Github projektu](https://github.com/bostrot/wsl2-distro-manager/releases/tag/v1.8.14).

{: .box-info}
Wiele płyt głównych domyślnie ma wyłączoną opcję wirualizacji. Opcja ta zwykle znajduje się w BIOSie w zaawansowanych ustawieniach procesora. Włącz ją zanim przejdziesz do dalszej instalacji.

Przy pierwszym uruchomieniu, jeśli nie miałeś wcześniej systemie WSL, **WSL Manager** przeprowadzi cię przez proces instalacji (wymagany będzie restart komputera). Po ponownym uruchomieniu przejdź do ustawień i zaznacz opcję **GuiAplications** na **true**.

![axrtWSL1](/assets/img/axrtWSL1.png)

Dodaj nową instancję WSL. Na poniższym screenie widzisz, że ja nazwałem swoją instancję *ubuntu*, wybrałem instalację *Ubuntu 24.04* i wpisałem swoją nazwę użytkownika, którą będę się posługiwał w linuksowym podsystemie.

![axrtWSL2](/assets/img/axrtWSL2.png)

Korzystając z windowsowej przeglądarki ściągnij ze strony [https://axrt.org/development/owb/x86_64/](https://axrt.org/development/owb/x86_64/) najnowsze archiwa z pakietem **LibAxRT**, bibliotekami **OWB-Libs**, przeglądarką **OWB** i launcherem dla OWB **StartOWB**.

![axrtWSL3](/assets/img/axrtWSL3.png)

Skopiuj pakiet **LibAxRT** oraz plik **StartOWB** do katalogu domowego użytkownika podsystemu WSL. Masz dostęp do katalogów WSL z poziomu Exploratora Plików Windows. Katalog *ubuntu* znajduje się po lewej stronie okna Eksploratora plików, pod nazwami dysków. 

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

- Przenieś plik **StartOWB** do katalogu z Odyssey Web Browser (*/home/username/Work/owb-x86_64*).

![axrtWSL10](/assets/img/axrtWSL10.png)

Możesz teraz uruchomić Odyssey Web Browser z poziomu terminala. Przejdź do katalogu z OWB i uruchom plik StartOWB.  
```
cd Work/owb-x86_64  
./StartOWB
```

Możesz też utworzyć skrót na pulpicie. Pamiętaj, aby w ścieżce wpisać swoją własną nazwę użytkownika.

```
"C:\Program Files\WSL\wslg.exe" -- "/home/username/Work/owb-x86_64/StartOWB"
```

![axrtWSL12](/assets/img/axrtWSL12.png)

{: .box-success}
Pomiędzy aplikacjami AxRT, a systemem hostującym działa schowek. Możesz używać schowka za pomocą CTRL+C, CTRL+V po stronie hosta oraz AMIGA+C, AMIGA+V po stronie AxRT.

Zapraszam na forum [AROS World](https://www.arosworld.org), gdzie możesz zadać dodatkowe pytania na temat użytkowania AROSa, AxRT i OWB. Możesz też tam zgłaszać napotkane błędy w działaniu.
  
![axrtWSL11](/assets/img/axrtWSL11.png)

## Problemy z dźwiękiem?

Możesz nie mieć dźwięku, np. podczas odtwarzania filmów na YouTube. Dzieje się tak dlatego, że WSLg w obecnej wersji obsługuje PulseAudio, ale nie ALSA. Istnieje wtyczka libasound2 (biblioteka ALSA), która przenosi połączenie z ALSA na PulseAudio. Wtyczka nazywa się pulse. Musisz więc zainstalować wtyczkę, uruchamiając w terminalu polecenie:
```
sudo apt install libasound2-plugins
```
i włączyć ją ręcznie, tworząc w katalogu domowym plik **.asoundrc** z poniższą zawartością:
```
pcm.default pulse
ctl.default pulse
```
Na koniec należy zrestartować system WSL.  

{: .box-note}
Pobierz gotowe archiwum z plikiem **.asoundrc** i rozpakuj je w katalogu domowym:  
[.asoundrc](/assets/asoundrc.zip "download")

