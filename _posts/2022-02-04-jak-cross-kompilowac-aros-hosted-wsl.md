---
layout: post
title: Jak cross-kompilować dla AROS
subtitle: w Windows 10 / 11 z WSL2
lang: pl
ref: tutWSLcross
---

Cross-kompilowanie to proces tworzenia oprogramowania na jednym systemie, które jest przeznaczone do uruchamiania na innym systemie. Możesz kompilować oprogramowanie dla AROS korzystając z portu AROSa hostowanego w systemie Linux. Pod Windowsem jest to możliwe przy użyciu WSL2 (Windows Subsystem for Linux 2).

## Wymagania

Aby zainstalować WSL2 potrzebujesz:
- System operacyjny Windows 10 May 2020 (2004) lub nowszy
- Komputer wspierający Hyper-V Virtualization
- Zainstalowany sterownik dla vGPU

{: .box-note}
Aby uruchamiać aplikacje GUI w systemie Linux, należy najpierw zainstalować poniższy sterownik pasujący do systemu. Umożliwi to korzystanie z wirtualnego 
procesora graficznego (vGPU), dzięki czemu można korzystać ze sprzętowej akceleracji renderowania OpenGL.  
[Sterownik GPU Intel](https://www.intel.com/content/www/us/en/download/19344/intel-graphics-windows-dch-drivers.html)  
[Sterownik GPU AMD](https://www.amd.com/en/support)  
[Sterownik GPU NVIDIA](https://www.nvidia.com/Download/index.aspx?lang=en-us)  
  
## Instalacja WSL2

Otwórz *Wiersz polecenia* z uprawnieniami administratora i wpisz:
```
wsl --install -d ubuntu-22.04
```
Po zakończeniu uruchom ponownie komputer. Zaloguj się do systemu Windows, a wiersz polecenia otworzy się ponownie. Tym razem zostaniesz przeprowadzony przez konfigurację Ubuntu za pomocą nazwy użytkownika i hasła (nie muszą one być takie same jak nazwa użytkownika i hasło systemu Windows).

Teraz możesz uruchomić aplikację *Ubuntu* z menu Start, aby rozpocząć, lub zainstalować aplikację *Microsoft Terminal*.

Aby zaktualizować pakiety w twoim świeżo zainstalowanym Ubuntu wpisz jeszcze polecenie:
```
sudo apt update && sudo apt upgrade
```

{: .box-note}
Od strony Windows masz łatwy dostęp do systemu plików Ubuntu wpisując w Eksploratorze plików **\\\wsl$\Ubuntu-22.04**

## Instalacja AROS hosted x86_64

Zainstaluj wszystkie potrzebne pakiety. Możesz to zrobić jedną komendą:
```
sudo apt install git gcc g++ make gawk bison flex bzip2 netpbm autoconf automake libx11-dev libxext-dev libc6-dev liblzo2-dev libxxf86vm-dev libpng-dev gcc-multilib libsdl1.2-dev byacc python3-mako libxcursor-dev cmake genisoimage dh-make unzip
```
Na potrzeby tej instalacji załóż w swoim katalogu użytkownika w Ubuntu katalog *myprojects*, a w nim katalog *arosbuilds*. Następnie sklonuj repozytorium AROS z githuba **deadwood**'a i skopiuj plik *rebuild.sh* z katalogu *AROS* do katalogu *arosbuilds*. Poniżej ciąg komend którymi to zrobisz:

```
mkdir myprojects
cd myprojects
mkdir arosbuilds
cd arosbuilds
git clone https://github.com/deadwood2/AROS.git AROS
cp ./AROS/scripts/rebuild.sh .
```
Uruchom skrypt *rebuild.sh*:
```
./rebuild.sh
```
Wybierz opcję *toolchain-core-x86_64*
```
1) toolchain-core-x86_64
```
Po zakończeniu ponownie uruchom skrypt *rebuild.sh*, tym razem wybierz opcję *core-linux-x86_64 (DEBUG)*
```
2) core-linux-x86_64 (DEBUG)
```

{: .box-note}
W czasie kompilacji wymagane jest połączenie sieciowe, gdyż pobierane są z sieci dodatkowe źródła.

Po zakończenu operacji AROS jest już zainstalowany. Możesz go uruchomić wykonując plik *AROSBootstrap*
```
cd core-linux-x86_64-d/bin/linux-x86_64/AROS
./boot/linux/AROSBootstrap
```

{: .box-note}
Jeśli chcesz uruchomić AROS z określoną ilocią pamięci użyj parametru *-m*, np, **"-m 1024"** dla 1GB RAM

![AROS hosted](/assets/img/aroshosted.jpg)
*AROS x86_64 w WSL2*

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

Żebyś mógł wykonać skrypt, zmień atrybuty stworzonego pliku:
```
chmod 755 startaros.sh
```

Powyższy skrypt do działania wymaga też zainstalowania dodatkowych pakietów:
```
sudo apt install net-tools uml-utilities
```

Po stronie AROS w *Prefs/Network* wybierz interface **tap.device** i ustaw ręcznie adresy IP tak jak na poniższym screenie:

![Konfiguracja sieci](/assets/img/networkhosted.jpg)
*Konfiguracja sieci w AROS hosted*

Kolejnym krokiem będzie skompilowanie contrib, aby mieć do dyspozycji całe AROSowe SDK.

```
git clone https://github.com/deadwood2/contrib.git contrib
cd contrib
git checkout master
```

Pobrany katalog contrib przenieś do katalogu AROS (tak aby mieć *AROS/contrib*). Następnie przejdź do katalogu *core-linux-x86_64-d* i uruchom:
```
make contrib
```

{: .box-note}
Jeśli masz wielordzeniowy procesor możesz użyć komendy **make** z parametrem *-j* (np. **"make -j4 contrib"**), aby nieco przyspieszyć proces budowy wykorzystując więcej wątków.

Utwórz katalog *cross-x86_64-aros* na tym samym poziomie co katalogi *AROS* i *core-linux-x86_64-d*.
```
mkdir cross-x86_64-aros
```
Następnie stwórz w nim plik o nazwie x86_64-aros-gcc z następującą zawartością:
```
exec /home/username/myprojects/arosbuilds/toolchain-core-x86_64/x86_64-aros-gcc --sysroot=/home/username/myprojects/arosbuilds/core-linux-x86_64-d/bin/linux-x86_64/AROS/Development "$@"
```
I ustaw mu atrybuty:
```
chmod 755 x86_64-aros-gcc
```

Ostatnim krokiem będzie dopisanie katalogu cross-x86_64-aros do PATH. Żeby to zrobić na stałe otwórz plik **.bashrc**, który znajduje się w twoim katalogu domowym użytkownika i na samym końcu dodaj linijkę:

```
export PATH=$PATH:/home/username/myprojects/arosbuilds/cross-x86_64-aros
```

{: .box-note}
Pamiętaj żeby zmienić w ścieżkach *username* na swoją nazwę użytkownika.

Jeśli wszystko poszło dobrze, wpisując **x86_64-aros-gcc** powinieneś mieć działający kompilator.
```
x86_64-aros-gcc -c hello.c -o hello
```
