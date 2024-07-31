---
layout: post
title: Oddysey Web Browser w AROS Linux hosted
subtitle: instrukcja instalacji
lang: pl
ref: tutOWBh
---

Do zainstalowania systemu **AROS** w wersji hostowanej przez system linuks, użyjemy najnowszej dystrybucji **Linux Mint 22 "Willma" (Cinnamon Edition)**. Upewnij się w **Update Manager**, że system jest w pełni aktualny. 

![hosted1](/assets/img/hosted1.png)

Uruchom **Software Manager** i doinstaluj pakiet **Uml-utilities**.

![hosted2](/assets/img/hosted2.png)

Korzystając z linuksowej przeglądarki ściągnij ze strony [https://axrt.org/development/owb/x86_64/](https://axrt.org/development/owb/x86_64/) najnowsze archiwa z **AROS** oraz **OWB**.

![hosted4](/assets/img/hosted4.png)

Wypakuj z archiwum katalog AROS do /home/username/ (gdzie *"username"* to twoja nazwa użytkownika w katalogu domowym).

![hosted5](/assets/img/hosted5.png)

Archwum z OWB wypakuj w dowolne miejsce w strukturze katalogów AROS. Ja wypakowałem do *AROS/Extras/Networking/Apps/* i zmieniłem nazwę katalogu z **owb-x86_64** na **OWB**.

![hosted6](/assets/img/hosted6.png)

Skopiuj do *AROS/boot/linux/* plik **startaros.sh**, który zawiera skrypt sieciowy po stronie linuksa i uruchamia AROSa.

{: .box-note}
Pobierz plik:  
[startaros.sh](/assets/startaros.sh "download")

![hosted7](/assets/img/hosted7.png)

Otwórz plik w edytorze tekstu i zmień nazwy interfejsów sieciowych na takie, które występują w twoim systemie.

![hosted8](/assets/img/hosted8.png)

Aby sprawdzić nazwy swoich interfejsów sieciowych uruchom **Advanced Network Configuration**.

![hosted9](/assets/img/hosted9.png)

Zaznacz nazwę połaczenia sieciowego i kliknij w ikonę ustawień. W polu *Device* znajduje się nazwa interfejsu sieciowego. W moim przypadku karta wifi ma nazwę **wlp2s0**, a karta ethernet **eno1**. U ciebie te nazwy mogą być inne. Pamiętaj, aby poprawnie wpisać je do skryptu.

![hosted10](/assets/img/hosted10.png)

Kliknij prawym klawiszem myszy na właściwości pliku **startaros.sh** i w zakładce *Permissions* zaznacz pole *Allow executing file as program*.

![hosted11](/assets/img/hosted11.png)

Dodaj na pulpicie ikonę uruchamiającą AROSa. Kliknij prawym klawiszem myszy na pulpicie i wybierz opcję *Create a new launcher here...* W polu **Command** wpisz */home/AROS/username/boot/linux/startaros.sh* (pamiętaj o zmianie w tej ścieżce nazwy użytkownika na własną). Zaznacz pole "Launch in terminal" i wciśnij "OK".

![hosted12](/assets/img/hosted12.png)

Konfiguracja po stronie linuksa na tym się kończy. Po uruchomieniu systemu z ikony w nowym oknie otworzy się AROS jak na poniższym screenie. Wygląd systemu dostosujesz w preferencjach AROSa. 

Rozdzielczość ekranu: *System/Prefs/ScreenMode*  
Rozmiar czcionek: *System/Prefs/Font*  
Rozmiar pozostałych czcionek i inne ustawienia: *System/Prefs/Zune*  

![hosted13](/assets/img/hosted13.png)

Istotne są ustawienia sieciowe po stronie AROSa. Ustaw je w *System/Prefs/Network* dokładnie tak jak na poniższym screenie:

![networkhosted](/assets/img/network.png)

Przetestuj działanie internetu. Uruchom *System/System/Shell* i wykonaj polecenie **ping**, np. "ping google.com". 

![ping](/assets/img/ping.png)

Jeśli wszystko skonfigurowałeś poprawnie i internet działa, możesz teraz uruchomić Oddysey Web Browser. Pamiętaj, że pierwsze uruchomienie OWB trwa dłużej niż zwykle, gdyż pobierane są w tym czasie czcionki.

![hosted14](/assets/img/hosted14.png)

Możesz teraz cieszyć się OWB na swoim nowoczesnym sprzęcie. Zapraszam na forum **[AROS World](https://arosworld.org)**, gdzie możesz zadać dodatkowe pytania na temat użytkowania AROSa i OWB. Możesz też tam zgłaszać napotkane błędy w działaniu.

![hosted15](/assets/img/hosted15.png)

