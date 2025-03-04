---
layout: post
title: AROS x86 - październik 2024
subtitle: podsumowanie miesiąca
lang: pl
ref: 1024
---

Dawno nie działo się tak wiele jednocześnie. W tym miesiącu dostaliśmy zbiorczą aktualizację do wersji bazowej systemu ABIv0, mamy nową wersję przeglądarki internetowej, a na dodatek zaczęły się pojawiać wersje x64 ważnego oprogramowania. Parafrazując slogan Commodore: "Are you keeping up with the AROS?". Mam nadzieję, że tak!

Deadwood przygotował Update 2 dla aktualnej wersji bazowej 32-bitowego AROSa (ABIv0_20220318-1), który jest zbiorem poprawek z ostatnich 5 miesięcy (między innymi dla Wanderera, Zune oraz biblioteki języka C). Update 2 zawiera również update 1, dzięki czemu można ją zastosować bezpośrednio na istniejącej instalacji 20220318-1. 

{: .box-success}
Aby pobrać ISO systemu oraz update 2 i zapoznać się z pełną listą zmian, odwiedź:  
[https://github.com/deadwood2/AROS/releases/tag/ABIv0_20220318-1](https://github.com/deadwood2/AROS/releases/tag/ABIv0_20220318-1)

Największym wydarzeniem jest niewątpliwie [Odyssey Web Browser w wersji 2.0](https://archives.arosworld.org/?function=showfile&file=network/browser/owb-2.0.i386-aros.zip). Silnik Webkit został zaktualizowany od sierpnia 2015 r. do lutego 2019 r. (ponad 50 000 zmian!). W rezultacie Youtube, a także wiele innych nowoczesnych witryn ponownie działa w przeglądarce AROSa. Dodatkowo, przeportowany został media player z przeglądarki Wayfarer 1.21 oraz włączona akceleracja dekodowania oparta o instrukcje SSE. Do poprawnego jej działania wymagana jest nowa aktualizacja systemu.  

W dzisiejszym świecie, gdzie strony internetowe stają się bardziej wymagające z dnia na dzień, aktualizacja przeglądarki internetowej to niekończąca się podróż. Warto rozważyć [donate dla Deadwooda](https://www.paypal.com/paypalme/4deadwood), gdyż aktualizacja silnika Webkit do wersji dzisiejszej to jeszcze niezliczone godziny pracy. Do rozwoju możesz się przyczynić także pobierając i testując przeglądarkę. Nawet jeśli nie używasz AROSa na codzień, warto spróbować choćby na wirtualnej maszynie pod Windowsem.

<div class="embed-container">
<iframe width="700" height="480" src="https://www.youtube.com/embed/cA1lAy36Pg0" frameborder="0"> </iframe>
</div>

W najbliższym czasie możemy spodziewać się oficjalnego wydania OWB 2.0 w wersji 64-bit. Dlaczego przyszłość OWB znajduje się w 64-bit doskonale wyjaśnił Deadwood w swoim [artykule o JavaScript i JIT](https://arosnews.github.io/64bit-odyssey-and-javascript-story/). Na szczęście coraz wieksza ilość oprogramowania jest kompilowana dla 64-bitowej wersji AROSa. Za sprawą Daremona jest już 64-bitowy [Python](https://archives.arosworld.org/?function=showfile&file=development/language/python-2.5.2.x86_64-aros-v11.zip) i [Perl](https://archives.arosworld.org/?function=showfile&file=development/language/perl-5.7.2.x86_64-aros-v11.zip), dzięki czemu mamy cały natywny toolchain dla 64-bit. Ponadto Daremon skompilował bibliotekę audio [libMAD](https://archives.arosworld.org/?function=showfile&file=development/library/libmad-0.15.1b.x86_64-aros-v11.zip), a gracze ucieszą się z 64-bitowych wersji [Doom 3](https://archives.arosworld.org/?function=showfile&file=game/fps/adoom3-1.5.3.x86_64-aros-v11.zip), silników [GemRB](https://archives.arosworld.org/?function=showfile&file=game/roleplaying/gemrb-0.8.8-0.x86_64-aros-v11.zip), [ResidualVM](https://archives.arosworld.org/?function=showfile&file=emulation/misc/residualvm-0.3.1-1.x86_64-aros-v11.zip) i [ScummVM](https://archives.arosworld.org/?function=showfile&file=emulation/misc/scummvm-1.9.0-1.x86_64-aros-v11.zip). ALB42 swój czytnik ePub [Legadon](https://home.alb42.de/files/Legadon03_AROS64.lha) także udostepnił w wersji dla ABIv11. Czy przyszły rok będzie rokiem totalnej przesiadki na 64-bity?

Wracając do 32-bitowej teraźniejszości:  

Serk118 zaktualizował swoje porty [GLFW 3.4](https://archives.arosworld.org/?function=showfile&file=development/library/lib_glfw_3_4.i386-aros.zip) oraz [Raylib 5.0](https://archives.arosworld.org/?function=showfile&file=development/library/lib_raylib5.i386-aros.zip).

![Ralib5](/assets/img/1024/raylib.png)
*Raylib 5*

Raylib to biblioteka programistyczna pozwalająca cieszyć się programowaniem gier wideo; bez wyszukanego interfejsu, bez wizualnych pomocników, bez narzędzi gui lub edytorów... po prostu kodowanie w czysto spartański sposób. Z tym updatem dostajemy także:

> ## [rFXGen](https://archives.arosworld.org/?function=showfile&file=audio/rfxgen-aros.zip)
> (autor: raylibtech.itch.io/rfxgen, port by Serk118)

Prosty i łatwy w użyciu generator efektów dźwiękowych.

Funkcje:  
- Predefiniowane **ustawienia dźwiękowe** (Coin, Shoot, Explosion, PowerUp...)
- Obsługa wielu typów fal (kwadratowa, piłokształtna, sinusoidalna, szum)
- Do **5 slotów dźwiękowych** do przechowywania wygenerowanego dźwięku (zapis tymczasowy)
- Wczytywanie plików `.rfx` z parametrami generowania dźwięku
- Zapisywanie plików `.rfx` z parametrami generowania dźwięku (**104 bajty**)
- Eksport danych wave jako `.wav`, `.raw` lub `.h` (tablica bajtów)
- Konfigurowalna częstotliwość próbkowania, bity na próbkę i kanały podczas eksportu
- Wiele stylów GUI z obsługą niestandardowych (`.rgs`)
- Obsługa konwersji wsadowej `.rfx` do `.wav` z wiersza poleceń
- Odtwarzacz audio z wiersza poleceń dla plików `.wav`, `.ogg`, `.mp3` i `.flac`
- Całkowicie przenośny (jednoplikowy, bez zależności)**.
- **Darmowy i open-source**

> ## [RayGui](https://archives.arosworld.org/?function=showfile&file=development/misc/raygui.i386-aros.zip)
> (autor: github.com/raysan5/raygui, port by Serk118)

Raygui został zaprojektowany jako moduł pomocniczy dla Raylib do tworzenia prostych interfejsów GUI przy użyciu stylu graficznego raylib (proste kolory, zwykłe prostokątne kształty, szerokie granice...), ale może być dostosowany do innych silników/frameworków.

![RayGui](/assets/img/1024/raygui.png)
*RayGui*

> ## [kMusicPlayer](https://archives.arosworld.org/?function=showfile&file=utility/archive/cabextract1.11.i386-aros.zip)
> (autor: github.com/notkatsuu/kMusicPlayer, port by Serk118)

kMusicPlayer to wizualny odtwarzacz muzyki zbudowany z C i Raylib. Zapewnia prosty interfejs wizualny do odtwarzania ulubionych utworów muzycznych.  

Główne cechy:
- Odtwarzanie muzyki: Łatwe odtwarzanie ulubionych utworów. Obsługuje formaty .mp3 i .wav.
- Wizualizacja kształtu fali: Wizualizacja muzyki dzięki renderowaniu kształtu fali.
- Wątkowe ładowanie muzyki: Szybkie ładowanie muzyki dzięki ładowaniu wątkowemu.
- Proste sterowanie: Kontroluj odtwarzanie za pomocą prostych skrótów klawiaturowych w RayGUI.

> ## [Koala Seasons](https://archives.arosworld.org/?function=showfile&file=game/strategy/koala_seasons.i386-aros.zip)
> (autor: www.raylib.com, port by Serk118)

Walcz z żywiołami! Walcz z wrogami! Ocal świat! Jak długo uda ci się przetrwać? Ta gra została pierwotnie stworzona przez emegeme jako benchmark dla Raylib na urządzeniach z Androidem.  
  
Pozostałe nowości w AROS Archives:  

> ## [BeeBase](https://archives.arosworld.org/?function=showfile&file=office/database/beebase-1.1.lha) (v. 1.1)
> (autor: Steffen Gutman)

BeeBase to relacyjny, programowalny system baz danych z graficznym interfejsem użytkownika dla wszystkich systemów amigowych, a także dla Windows, Mac i Linux. Siła BeeBase leży w graficznym interfejsie użytkownika i możliwościach programowania. Umożliwia on przetwarzanie danych na różne sposoby, np. automatyczne obliczenia po wprowadzeniu danych przez użytkownika, generowanie raportów, importowanie i eksportowanie danych itp. 

![BeeBase](/assets/img/1024/beebase.png)
*BeeBase*

> ## [Amifish](https://archives.arosworld.org/?function=showfile&file=game/board/amifish.i386-aros.lha) (v. 2.0)
> (autor:	Domenico Lattanzi)

Amifish to program szachowy stworzony do gry w szachy na systemach amigowych, wykorzystujący moc jednego z najpotężniejszych silników szachowych na świecie: Stockfish, opracowanego przez Torda Romstada, Marco Costalbę, Joonę Kiiski i Gary'ego Linscotta. Silnik szachowy to program konsolowy, który gra w szachy, odbierając ciągi znaków jako polecenia i generując ciągi znaków na wyjściu jako wynik obliczeń. Stockfish i wiele innych silników jest kompatybilnych ze standardem o nazwie UCI (Universal Chess Interface). Nazwa Amifish powstała z połączenia słów Amiga i Stockfish (choć projekt jest otwarty dla wszystkich silników zgodnych ze standardem UCI), jest lekkim programem dla amatorów, stworzonym do zabawy w szachy, z zaimplementowanymi tylko najważniejszymi opcjami.

Do gry przeciwko komputerowi potrzebny jest silnik szachowy Stockfish, który również można [pobrać](https://archives.arosworld.org/?function=showfile&file=game/misc/stockfish5_aros-i386.zip) z AROS Archives.

![Amifish](/assets/img/1024/amifish.png)
*Amifish*

> ## [GemRB](https://archives.arosworld.org/?function=showfile&file=game/roleplaying/gemrb-0.8.8-0.i386-aros.zip) (v. 0.8.8-0)
> (autor: The GemRB Project)

GemRB to przenośna, open-source'owa implementacja 8 wersji silnika Infinity Engine firmy Bioware. Uruchamia gry **Baldur's Gate**, **Icewind Dale** i **Planescape: Torment** oraz ich rozszerzenia i mody. Silnik wymaga plików z danymi z oryginalnych gier. Port dla AROSa przygotował Daremon.

> ## [Legadon](https://home.alb42.de/files/Legadon03_AROS.lha) (v. 0.3)
> (autor: ALB42)

Prosty czytnik ePub dla AROS. ePuby to po prostu pliki zip z plikami XML i HTML, które opisują książkę elektroniczną. Legadon wyodrębnia tekst z HTML i pokazuje go użytkownikowi jako plain tekst w polu tekstowym.

> ## [CabExtract](https://archives.arosworld.org/?function=showfile&file=utility/archive/cabextract1.11.i386-aros.zip) (v. 1.11)
> (autor: Stuart Caie, port by Farox)

Program do rozpakowywania plików Microsoft Cabinet. Pliki Cabinet (`.CAB`) są formą archiwum, którego Microsoft używa do dystrybucji swojego oprogramowania i rzeczy takich jak Windows Font Packs. Program cabextract rozpakowuje te pliki.

> ## [Unshield](https://archives.arosworld.org/?function=showfile&file=utility/archive/unshield.i386-aros.zip) (v. 1.5.1)
> (autor:	David Eriksson, port by Farox)

Narzędzie do wyodrębniania plików `.CAB` z pliku `.exe` InstallShield.

> ## [SetScreenMode](https://archives.arosworld.org/?function=showfile&file=utility/shell/setscreenmode.i386-aros.zip) (v. 1.0)
> (autor:	Nigel Tromans)

Set_Screen_Mode to mała aplikacja Hollywood do automatycznego ustawiania trybu ekranu podczas uruchamiania z wcześniej ustawionej listy.  

Uwaga: Set_Screen_Mode jest przydatny tylko wtedy, gdy instalacja AROS wykorzystuje natywną grafikę.  

Została stworzona, aby umożliwić maszynom, które są przenoszone między różnymi wyświetlaczami (takimi jak laptopy z wewnętrznym ekranem i zewnętrznie podłączonymi monitorami) automatycznie uruchamiać się w preferowanym trybie ekranu dla każdego z tych wyświetlaczy, a także pomóc w wyświetlaniu ekranu na ekranach, które są trudne w użyciu (na przykład takich, które nie są w stanie wyświetlić domyślnego trybu 640x480).  

Set_Screen_Mode odczyta dostępne tryby ekranu dostarczone przez wyświetlacz i porówna je z trybami wybranymi przez użytkownika na uporządkowanej liście. Możliwe jest również wymuszenie trybu, nawet jeśli nie ma go na liście lub całkowite zignorowanie trybu ustawionego dla Set_Screen_Mode.  
