---
layout: page
title: Jak zainstalować AROS hosted
subtitle: w Windows 10 / 11 z WSL2
lang: pl
ref: tutWSLh
---

![hosted1](/assets/img/hosted1.png)

![hosted2](/assets/img/hosted2.png)

![hosted3](/assets/img/hosted3.png)

![hosted4](/assets/img/hosted4.png)

![hosted5](/assets/img/hosted5.png)

![hosted6](/assets/img/hosted6.png)

![hosted7](/assets/img/hosted7.png)

![hosted8](/assets/img/hosted8.png)

![hosted9](/assets/img/hosted9.png)

![hosted10](/assets/img/hosted10.png)

![hosted11](/assets/img/hosted11.png)

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
