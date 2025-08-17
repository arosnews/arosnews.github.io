---
layout: post
title: Jak przygotować pendrive USB
subtitle: z AROS ABIv11
lang: pl
ref: tutPendrive
---

AROS ABIv11 można pobrać w postaci pliku .iso i przygotować z niego bootowalny CD. Co jednak jeśli nie mamy w swojej maszynie z AROS napędu CD lub z innych powodów wolimy stworzyć bootowalny pendrive USB z systemem? Nic prostszego - wystarczy zainstalować AROS na dysku USB w podobny sposób jak gdybyśmy instalowali go na dysku twardym. W tym celu najlepiej wykorzystać maszynę wirtualną.

## Krok 1: Pobranie i instalacja VirtualBox

VirtualBox to darmowy i otwarty program do tworzenia i uruchamiania wirtualnych maszyn na komputerze. Aby go pobrać możesz odwiedzić [oficjalną stronę pobierania VirtualBox](https://www.virtualbox.org/wiki/Downloads) lub [Oracle Technology Network](https://www.oracle.com/virtualization/technologies/vm/downloads/virtualbox-downloads.html). Tam znajdziesz linki do plików instalacyjnych i źródeł kodu dla różnych platform. Ja pobrałem i zainstalowałem wersję dla Windows. Jeśli masz problemy z instalacją odsyłam do [tego poradnika](https://itsfoss.com/install-virtualbox-windows/).

## Krok 2: Utworzenie maszyny wirtualnej z systemem AROS

![Install](/assets/img/64pend2__.png)

Klikamy przycisk *New* w celu utwrzenia nowej maszyny wirtualnej. Wskazujemy nasz pobrany plik .iso z AROS ABIv11, w polu **Type:** wybieramy *Other*, a w polu **Version:** *Other/Unknown (64-bit)*.

![Install](/assets/img/64pend3__.png)

Pamięć i liczbę procesorów ustawiamy jak powyżej.

![Install](/assets/img/64pend4__.png)

Jeśli mamy zamiar wykorzystać naszą wirtualną maszynę tylko do przygotowania pendrive możemy nie tworzyć wirtualnego dysku.

![Install](/assets/img/64pend5__.png)

![Install](/assets/img/64pend6__.png)

Nasza wirtualna maszyna jest gotowa. AROS odpali się na tej domyślnej konfiguracji.

## Krok 3: Instalacja AROS na pendrive USB

![Install](/assets/img/64pend7__.png)

Wkładamy nasz pendrive USB i zaznaczamy go w opcjach **Devices/USB**. 

![Install](/assets/img/64pend8__.png)

Klikamy w ikonę InstallAROS. W oknie instalatora zaznaczamy *Wipe disk*, a w **Drive type:** *USB*. Uwaga! Instalator usunie wszystkie partycje znajdujące się na tym dysku USB.

![Install](/assets/img/64pend9__.png)

![Install](/assets/img/64pend10__.png)

Po resecie wirtualnej maszyny ponownie odpalamy InstallAROS tym razem zaznaczamy opcję *Use existing AROS partitions (on any drive)*.

![Install](/assets/img/64pend11__.png)

Tutaj możemy dodatkowo zaznaczyć *Install Debugging tools and Developer Software* jeśli mamy zamiar korzystać z tych narzędzi.

![Install](/assets/img/64pend12__.png)

![Install](/assets/img/64pend13__.png)

![Install](/assets/img/64pend14__.png)

![Install](/assets/img/64pend15__.png)

![Install](/assets/img/64pend16__.png)

Po zakończeniu kopiowania plików wciskamy ostatni raz *Proceed* i nasz pendrive USB z systemem jest gotowy. Możemy teraz zainstalować AROS na prawdziwym sprzęcie, najlepiej zaopatrzyć się w komputer z [rekomendowanej listy](https://en.wikibooks.org/wiki/Aros/Platforms/x86_Complete_System_HCL#Recommended_hardware_(64-bit)).
