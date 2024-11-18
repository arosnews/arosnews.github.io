---
layout: post
title: Odyssey Web Browser w AxRT Windows 11 (WSL2)
subtitle: instrukcja instalacji
lang: pl
ref: tutOWBaw
---

W tym krótkim tutorialu pokażę jak uruchomić Odyssey Web Browser na komputerze z Windows 11 z zainstalowanym WSL2. Jedną z prostszych metod na zainstalowanie WSL2 jest skorzystanie z **WSL Manager**. Możesz go pobrać bezpośrednio ze [strony Github projektu](https://github.com/bostrot/wsl2-distro-manager/releases/tag/v1.8.14). W tym tutorialu korzystałem z WSL Manager w wersji 1.8.14. 

{: .box-note}
Wiele płyt głównych domyślnie ma wyłączoną opcję wirualizacji. Opcja ta zwykle znajduje się w BIOSie w zaawansowanych ustawieniach procesora. Włącz ją zanim przejdziesz do dalszej instalacji.

Przy pierwszym uruchomieniu, jeśli nie miałeś wcześniej systemie WSL, **WSL Manager** przeprowadzi cię przez proces instalacji (wymagany będzie restart komputera). Po ponownym uruchomieniu przejdź do ustawień i zaznacz opcję **GuiAplications** na **true**.

![axrtWSL1](/assets/img/axrtWSL1.png)

Dodaj nową instancję WSL. Na poniższym screenie widzisz, że ja nazwałem swoją instancję *ubuntu*, wybrałem instalację *Ubuntu 24.04* i wpisałem swoją nazwę użytkownika, którą będę się posługiwał w linuksowym podsystemie.

![axrtWSL2](/assets/img/axrtWSL2.png)

Po pomyślnym zainstalowaniu WSL2 możesz przystąpić do instalacji AxRuntime i Odyssey. Możesz skorzystać z poniższego skryptu, który wykona za ciebie większość czynności. Pobierz go, a nastepnie umieść w katalogu domowym użytkownika w podsystemie linuks (/home/{username}).

{: .box-note}
Pobierz gotowe archiwum z plikiem **axrtsetup.sh** i rozpakuj je w katalogu domowym:  
[axrtsetup.zip](/assets/axrtsetup.zip "download")

Masz dostęp do katalogów WSL z poziomu Exploratora Plików Windows. Katalog *ubuntu* znajduje się po lewej stronie okna Eksploratora plików, pod nazwami dysków. 

![ubuntu](/assets/img/ubuntu.png)

Uruchom terminal z Ubuntu. 

![axrtWSL5](/assets/img/axrtWSL5.png)

- upewnij się, że jesteś w katalogu domowym do którego wypakowałeś plik axrtsetup.sh:
```
cd ~
```
- ustaw uprawnienia dla pliku **axrtsetup.sh**:
```
chmod +x axrtsetup.sh
```
- uruchom skrypt i poczekaj na zakończenie instalacji:
```
./axrtsetup.sh
```
Powninieneś w tej chwili mieć już zainstalowane AxRuntime i przeglądarkę Odyssey gotową do uruchomienia. Przejdź do katalogu z przeglądarką i uruchom ją za pomocą pliku **StartOWB**:
```
cd Work/owb-x86_64
./StartOWB
```

Alernatywnie, zamiast korzystać ze skryptu, wszystkie kroki możesz wykonać samodzielnie:  

Korzystając z windowsowej przeglądarki ściągnij ze strony [https://axrt.org/download/axrt/4.0/](https://axrt.org/download/axrt/4.0/) najnowsze archiwa z pakietem [**LibAxRT**](https://axrt.org/download/axrt/4.0/packages/libaxrt-4.0_41.12-1_amd64.deb), bibliotekami [**OWB-Libs**](https://axrt.org/download/axrt/4.0/other/OWB-Libs-for-x86_64-axrt.zip), przeglądarką [**OWB**]() i launcherem dla OWB [**StartOWB**](https://axrt.org/download/axrt/4.0/other/StartOWB).

![axrtWSL3](/assets/img/axrtWSL3.png)

Skopiuj pakiet **LibAxRT** oraz plik **StartOWB** do katalogu domowego użytkownika podsystemu WSL. Masz dostęp do katalogów WSL z poziomu Exploratora Plików Windows. Katalog *ubuntu* znajduje się po lewej stronie okna Eksploratora plików, pod nazwami dysków. 

![axrtWSL4](/assets/img/axrtWSL4.png)

Uruchom terminal z Ubuntu. 

![axrtWSL5](/assets/img/axrtWSL5.png)

Korzystając z terminala, wykonaj kolejno komendy:
- rozpakuj pakiet **LibAxRT**
```
sudo dpkg -i ~/libaxrt-4.0_41.12-1_amd64.deb
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

W katalogu owb-x86_64 zmień nazwę pliku "OWB.info.axrt" na "OWB.info". Dzięki temu będziesz miał ikonę z tooltype uruchamiającym OWB wykorzystujące CONCURRENT_JIT.

Możesz teraz uruchomić Odyssey Web Browser z poziomu terminala. Przejdź do katalogu z OWB i uruchom plik StartOWB.  
```
cd Work/owb-x86_64  
./StartOWB
```
## Problemy z odtwarzaniem dźwięku lub wideo na YouTube

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


Możesz też utworzyć skrót na pulpicie Windows. Pamiętaj, aby w ścieżce wpisać swoją własną nazwę użytkownika.

```
"C:\Program Files\WSL\wslg.exe" -- "/home/username/Work/owb-x86_64/StartOWB"
```

![axrtWSL12](/assets/img/axrtWSL12.png)

{: .box-success}
Pomiędzy aplikacjami AxRT, a systemem hostującym działa schowek. Możesz używać schowka za pomocą CTRL+C, CTRL+V po stronie hosta oraz AMIGA+C, AMIGA+V po stronie AxRT.

Zapraszam na forum [AROS World](https://www.arosworld.org), gdzie możesz zadać dodatkowe pytania na temat użytkowania AROSa, AxRT i OWB. Możesz też tam zgłaszać napotkane błędy w działaniu.
  
![axrtWSL11](/assets/img/axrtWSL11.png)

