---
layout: post
title: AROS x86 - luty 2024
subtitle: podsumowanie miesiąca
lang: pl
ref: 0224
---

Luty przynosi dobre wieści dla społeczności AROSa. Po blisko dwóch miesiącach wytężonej pracy mamy nową wersję bazową systemu AROS x86. Zgodnie z zapowiedziami w tej iteracji nastąpiło przejście na nową bibliotekę C. Ta zmiana nie przynosi na dzień dzisiejszy wielu widocznych zmian dla końcowego użytkownika, ale jest krokiem milowym w ogólnym rozwoju systemu. Programiści powinni pamiętać o zaktualizowaniu swoich SDK. 

{: .box-success}
Aby pobrać ISO i zapoznać się z pełną listą zmian, odwiedź:  
[https://github.com/deadwood2/AROS/releases/tag/ABIv0_20220318-1](https://github.com/deadwood2/AROS/releases/tag/ABIv0_20220318-1)

Wydanie nowej wersji bazowej zaowocowało pojawieniem się zaktualizowanej dystrybucji **AROS One 2.4**. Ze względu na ilość zmian zalecana jest czysta instalacja.

![AROS One 2.4](/assets/img/arosone24.jpg)
*AROS One 2.4*

{: .box-success}
Pełna lista zmian dla AROS One v2.4:  
[https://www.arosworld.org/infusions/forum/viewthread.php?thread_id=1124&pid=4150#post_3217](https://www.arosworld.org/infusions/forum/viewthread.php?thread_id=1124&pid=4150#post_3217)

Na [kanale YouTube Jamesa Mattsona](https://www.youtube.com/@jamesmattson6813/videos) można zobaczyć kilka filmików z działania AROS One 2.4.  

Lista [rekomendowanego sprzętu dla AROSa](https://en.wikibooks.org/wiki/Aros/Platforms/x86_Complete_System_HCL#Recommended_hardware) wzbogadziła się o dwie płyty główne: *ASUS P8Z68-V LX* oraz *Gigabyte GA-MA770T UD3/UD3P*. Moim zdaniem warto przyjrzeć się konstrucji ASUSa. Na tę chwilę jest to najnowszy i najmocniejszy sprzęt z listy rekomendowanych, niedrogi i szeroko dostępny w serwisach aukcyjnych. Jeśli planujesz zakup sprzętu pod AROSa będzie to najlepszy wybór. Rekomendowane płyty mają zapewnione długoterminowe wsparcie, wszystkie nowe wydania AROSa będą testowane pod względem kompatybilności z nimi. 

![P8Z68-v LX](/assets/img/p8z68v-lx.jpg)
*Płyta główna ASUS P8Z68-V LX*

Na blogu zamieściłem [tutorial na temat cross-kompilowania dla AROS pod Windows z WSL2](https://arosnews.github.io/jak-cross-kompilowac-aros-hosted-wsl/). W zasadzie robi się to tak samo jak pod linuksem, ale dla osób przywiązanych do Windowsa to takie przypomnienie, że WSL istnieje i działa dobrze :) Jeśli jesteś programistą, który chciałby zacząć przygodę z AROSem, to Krzysztof "deadwood" Śmiechowicz zamieścił na forum Aros World post z [zasobami dla programistów](https://www.arosworld.org/infusions/forum/viewthread.php?thread_id=1201). Są tam cenne informacje i linki, które z pewnością ułatwią start.

Tradycją już staje się cykliczna ankieta na "Irytujący bug miesiąca". Tym razem społeczność zdecydowała, że dobrze byłoby rozszerzyć opcje w preferencjach sieci o możliwość łatwego włączenia tetheringu USB.

![Irytujący bug miesiąca](/assets/img/ibotm0224.jpg)
*Irytujący bug miesiąca - luty 2024*

Dzięki tetheringowi możemy korzystać z internetu na AROSie przy pomocy telefonu z androidem podłączonego kablem USB. Pozwala to cieszyć się siecią nawet na urządzeniach, które nie posiadają wspieranej karty sieciowej. Tethering USB był obecny w AROS od dawna, ale przez brak opcji do łatwej aktywacji wielu użytkowników nie miało o jego istnieniu pojęcia. Teraz dzięki **deadwood**'owi można odpowiednią opcję "wyklikać".

![Tethering USB](/assets/img/te1.png)

![Tethering USB](/assets/img/te2.png)  
*Tethering USB*

Jeśli chcesz mieć wpływ na kolejność naprawy błędów, zachęcam do zarejestrowania sie na forum i wzięcia udziału w [kolejnym głosowaniu](https://www.arosworld.org/infusions/forum/viewthread.php?thread_id=1207).

W lutym nie zabrakło też nowych programów w AROS Archives. Znajdą coś dla siebie fani muzyki, grafiki, gier i demosceny :)

> ## [Feedback](http://archives.aros-exec.org/?function=showfile&file=demo/music/void-fb8-aros.i386-aros.zip) (nr 8)
> ## [Feedback](http://archives.aros-exec.org/?function=showfile&file=demo/music/void-fb11-aros.i386-aros.zip) (nr 11)
> (autor: Void)

Puni z demoscenowej grupy Void skompilował dla AROSa dwa music dyski swojej grupy. Są to Feedback wydanie 8 z 2019 r. oraz Feedback wydanie 11 z 2021 r. Obie produkcje zawierają po 10 utworów różnych autorów i zdecydowanie warto ich posłuchać. Jak zapewnia Puni wkrótce na AROS powinny pojawić się nowe produkcje od Void. Czekamy z niecierpliwością :)   

![Feedback](/assets/img/feedback11.jpg)
*Feedback 8 & 11*

> ## [Protrekkr 2](http://archives.aros-exec.org/?function=showfile&file=audio/tracker/ptk_v2.6.6.i386-aros.zip) (v. 2.6.6)
> (autor: Franck "hitchhikr" Charlet)

ProTrekkr to program typu tracker łączący w sobie syntezator programowy wraz z tradycyjnym trackerem sampli, który może (głównie) być używany do tworzenia muzyki elektronicznej (np. psytrance, trance goa, hard acid, IDM, chip, techno, jungle itp.) do małych intro, dem lub gier. Jest to mocno zmodyfikowana wersja starego NoiseTrekker 2, który został stworzony przez Juana Antonio Arguelles Rius aka Arguru. 

Zmiany w najnowszej wersji:
- Nieznacznie zmieniona instrukcja.
- Okno otwiera się teraz na środku ekranu.
- Rozmiar okna jest teraz zapamiętywany przy powrocie z pełnego ekranu.
- Dodano opcję ponownego wczytania ostatnio używanego ptk podczas uruchamiania.
- Dodano obsługę 512 ścieżek midi poprzez wybór banku.
- Naprawiono kilka błędów w samodzielnym odtwarzaniu.
- Dodano efekty 3F i 40 do ustawiania skali dwóch jednostek 303.
- W repozytorium brakowało pliku keyboards.txt.
- Dodano efekty 29, 2A i 2B do włączania/wyłączania kompresora ścieżek, ustawiania odpowiednio progu i współczynnika kompresji.
- Nie aktualizuje już interfejsu użytkownika z wątku audio (co naprawiło kilka problemów).
- Naprawiono błąd wyłączania nut dla jednostek 303.
- Dodano funkcję zamiany dwóch instrumentów we wzorcach.
- Przeprojektowano dużą część kodu.

![Protrekkr 2](/assets/img/ptk266.png)
*Protrekkr 2*

> ## [CAMD MIDI Driver](http://archives.aros-exec.org/?function=showfile&file=driver/audio/usbmidi.i386-aros.lha) (v. 1.4)
> (autorzy: hitchhikr, kalamatee, Alfred Faust, Neil Cafferkey)

Nowy sterownik MIDI dla AROSa.

> ## [SonosController](http://archives.aros-exec.org/?function=showfile&file=audio/misc/sonoscontroller.lha) (v. 1.4)
> (autor: Michael Rupp)

SonosController umożliwia sterowanie głośnikami Sonos z dowolnej Amigi podłączonej do tej samej sieci.

Wersja 1.4 to pierwsze wydanie dla AROS x86.

![SonosController](/assets/img/sonos.png)
*SonosController*


> ## [BOH](http://archives.aros-exec.org/?function=showfile&file=game/action/boh.i386-aros.lha) (v. 2.3)
> (autor: Simone Bevilacqua "Saimo")

BOH to dungeon crawler, w którym musisz rozwiązywać zagadki, zbierać przedmioty, otwierać przejścia, unikać pułapek, zabijać złych mistrzów i generowanych przez nich sługusów, a ostatecznie wyjść z labiryntów w jednym kawałku. Zachowaj zimną krew, unikaj wrogów tak bardzo, jak to możliwe, skup się na labiryntach, a w końcu dotrzesz do końca.

W Aros Archives pojawiła się najnowsza iteracja tej znanej gry oznaczona numerem 2.3. Jest to dobra okazja do odświeżenia sobie tego tytułu :)

![BOH](/assets/img/boh.jpg)
*BOH*

> ## [WCS](http://archives.aros-exec.org/?function=showfile&file=graphics/raytrace/wcs.multi-aros.lha) (v. 2.031)
> (autor: Alexander Fritsch “Selco”)

To jest nowo skompilowana wersja World Construction Set 2.031. Aplikacja została oryginalnie opracowana przez Gary'ego R. Hubera i Chrisa "Xenona" Hansona z Questar Productions. WCS służy do tworzenia fraktalnych krajobrazów, podobnie jak Scenery Animator, Vista Pro i Panorama.

Program może być skomplikowany w obsłudze dla początkujących, polecam zapoznać się z [tutorialem](http://www.bertinettobartolomeodavide.it/graficadigitale/amiga/WCS/Tutorial%20World%20Construction%20Set.html). Tutorial w języku angielskim jest także załączony do archiwum z programem.

![WCS](/assets/img/wcs.jpg)
*WCS - World Construction Set*

> ## [Odyssey Web Browser](http://archives.aros-exec.org/?function=showfile&file=network/browser/owb-1.26.i386-aros.zip) (v. 1.26)
> (autorzy: WebKit Team, Fabien Coeurjoly, Krzysztof Śmiechowicz)

Wydana została nowa wersja Odyssey Web Browser. Poprzednia wersja została udostępniona w 2016 roku, a nowe wydanie przynosi ponowną kompilację z nowszym SDK i szereg poprawek błędów. Ta wersja Odyssey do działania wymaga najnowszego wydania systemu bazowego AROS.  

Przeglądarka ma być dalej rozwijana. Kolejnym krokiem będzie wydanie 64-bitowej wersji Odyssey dla systemów AROS, Linux i Windows oraz doprowadzenie jej do poziomu stabilności, który pozwoli na codzienne surfowanie po stronach związanych z Amigą. Wszelkie ulepszenia, które zostaną wprowadzone, będą również dostępne dla 32-bitowej wersji OWB.

![OWB](/assets/img/owb126.jpg)
*Odyssey Web Browser*

{: .box-success}
Kilka innych aplikacji z AROS Archives także zostało przekompilowanych dla zachowania kompatybilności z najnowszym buildem:
- [Acidwarp](http://archives.aros-exec.org/?function=showfile&file=demo/misc/acidwarp.i386-aros.zip) - kilka ciekawych efektów graficznych.  
- [Bad Apple](http://archives.aros-exec.org/?function=showfile&file=demo/misc/badapple.i386-aros.zip) - słynne demo/animacja Bad Apple.  
- [Dosbox](http://archives.aros-exec.org/?function=showfile&file=emulation/computer/dosbox.i386-aros.zip) - emulator systemu DOS.  
- [wput](http://archives.aros-exec.org/?function=showfile&file=network/ftp/wput-0.3.4c.i386-aros.zip) - klient FTP działający z wiersza poleceń.  
- [JetPac - The Return](http://archives.aros-exec.org/?function=showfile&file=game/action/jetpac.i386-aros.zip) - remake klasycznej gry z ZX Spectrum.  
