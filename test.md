---
layout: page
title: Jak zainstalować AROS hosted
subtitle: w Windows 10 / 11 z WSL2
lang: pl
ref: tutWSLh
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

![hosted7](/assets/img/hosted7.png)

Otwórz plik w edytorze tekstu i zmień nazwy interfejsów sieciowych na takie, które występują w twoim systemie. Nakońcu skrypu w ścieżce dostępu do pliku zmień nazwę użytkownika na własną.

![hosted8](/assets/img/hosted8.png)

Aby sprawdzić nazwy swoich interfejsów sieciowych uruchom **Advanced Network Configuration**.

![hosted9](/assets/img/hosted9.png)

Zaznacz nazwę połaczenia sieciowego i kliknij w ikonę ustawień. W polu *Device* znajduje się nazwa interfejsu sieciowego. W moim przypadku karta wifi ma nazwę **wlp2s0**, a karta ethernet **eno1**. U ciebie te nazwy mogą być inne. Pamiętaj, aby poprawnie wpisać je do skryptu.

![hosted10](/assets/img/hosted10.png)

Kliknij prawym klawiszem myszy na właściwości pliku **startaros.sh** i w zakładce *Permissions* zaznacz pole *Allow executing file as program*.

![hosted11](/assets/img/hosted11.png)

Dodaj na pulpicie ikonę uruchamiającą AROSa. Kliknij prawym klawiszem myszy na pulpicie i wybierz opcję *Create a new launcher here...* W polu **command" wpisz */home/AROS/username/boot/linux/startaros.sh* (pamiętaj o zmianie w tej ścieżce nazwy użytkownika na własną).

![hosted12](/assets/img/hosted12.png)

![hosted13](/assets/img/hosted13.png)

![hosted14](/assets/img/hosted14.png)

![hosted15](/assets/img/hosted15.png)

## Instalacja Odyssey Web Browser

Ściągnij archiwum z OWB:  
[https://axrt.org/development/OWB-1.25-20231230.x86_64-aros.zip](https://axrt.org/development/OWB-1.25-20231230.x86_64-aros.zip)  
Przejdź do katalogu *core-linux-x86_64-d\bin\linux-x86_64\AROS*. Znajduje się tutaj cała struktura katalgów AROSa. Możesz tu utworzyć katalog *Applications* i rozpakować do niego archiwum OWB. Możesz to zrobić zarówno od strony WSL2/Ubuntu jak i od strony Windows. 

Aby **Odyssey Web Browser** działał prawidłowo AROS potrzeuje 1GB pamięci RAM, więc należy uruchamiać go z parametrem **"-m 1024"**. Potrzebujesz też działającego internetu. Po stronie AROS w *Prefs/Network* wybierz interface **tap.device** i ustaw adresy IP tak jak na poniższych screenach.

Po stronie Ubuntu możesz użyć skryptu, który skonfiguruje połączenie sieciowe dla AROS. Możesz utworzyć w swoim katalogu domowym skrypt **startaros.sh**, który ustawi sieć, a następnie uruchomi AROS z 1GB pamięci RAM:

```
#!/bin/sh

NETON=`ifconfig | grep aros0`

if [ "$NETON" = "" ]; then
    echo "Installing bridge network... (sudo access required)"
    sudo tunctl -b -u "$USER" -t aros0
    sudo ifconfig aros0 192.168.166.1
    sudo iptables -t nat -A POSTROUTING -o eth0 -s 192.168.166.0/2 -j MASQUERADE
    sudo iptables -t nat -A POSTROUTING -o wlan0 -s 192.168.166.0/2 -j MASQUERADE
    sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"
fi

cd myprojects/arosbuilds/core-linux-x86_64-d/bin/linux-x86_64/AROS
./boot/linux/AROSBootstrap -m 1024
```

{: .box-note}
Jeśli twój interface sieciowy ma inną nazwę niż **eth0**, pamietaj żeby zmienić to w skrypcie.
