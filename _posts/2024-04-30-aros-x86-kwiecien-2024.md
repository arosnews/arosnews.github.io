---
layout: post
title: AROS x86 - kwiecień 2024
subtitle: podsumowanie miesiąca
lang: pl
ref: 0424
---

W kwietniu 2024 roku, choć nie pojawiła się nowa wersja AROS dla x86, to i tak działo się bardzo wiele. Deadwood kontynuuje prace nad prototypem emulatora x86 dla 64-bitowej wersji systemu. W niedługim czasie możemy się też spodziewać od niego zbiorczego pakietu poprawek do ostatniego builda. Społeczność AROSa jest niezwykle aktywna, a to przynosi efekty w postaci licznych portów i aktualizacji oprogramowania. Dzięki zaangażowaniu nowych użytkowników, którzy przeportowali lub uaktualnili starsze aplikacje, AROS zyskał sporo nowych możliwości. Przyjrzyjmy się bliżej, co pojawiło się w tym miesiącu!

Z sieci zniknęła strona z której zwykle można było pobrać dystrybucję Tiny AROS. Nie mamy się jednak czym przejmować, jak zapewnia autor dystrybucji - Amiwell79 - nowa strona, pod nowym adresem, pojawi się w najbliższych dniach. Gdy to nastąpi aktualny link znajdziecie na tym blogu.

W kwietniowej ankiecie na "irytującego buga miesiąca" zostały wytypowane dwa:  
*#116 (Wanderer: Allow deleting by pressing Del key)*  
*#105 (DiskInfo showing OFS instead of FAT)*  
Łatki do tych błędów zostały przygotowane przez **Deadwooda** i można je już pobrać z forum AROSWorld w wątku poświęconym [kwietniowej ankiecie](https://www.arosworld.org/infusions/forum/viewthread.php?thread_id=1228&pid=4744). Trafią też do kolejnego builda, gdy tylko zostanie wydany.

![Irytujący bug miesiąca](/assets/img/ibotm0424.png)
*Irytujący bug miesiąca - kwiecień 2024*

Jeśli chcesz mieć wpływ na kolejność naprawy błędów, zachęcam do zarejestrowania sie na forum i wzięcia udziału w kolejnym głosowaniu: [Link do aktualnej ankiety](https://www.arosworld.org/infusions/forum/viewthread.php?thread_id=1246&pid=5066). 

W AROS Archives pojawiło się wiele interesujących pozycji, tym razem każdy znajdzie coś ciekawego dla siebie. Nowości w AROS Archives z kwietnia:

> ## [ScummVM](http://archives.aros-exec.org/?function=showfile&file=emulation/misc/scummvm-1.9.0-1.i386-aros.zip) (v.1.9.0)
> (autorzy: Max Horn, Eugene Sandulenko i wielu innych)

ScummVM – interpretator umożliwiający uruchomienie na współczesnych systemach gier typu wskaż i kliknij. Początkowo zaprojektowany, aby obsługiwać gry firmy LucasArts korzystające z silnika SCUMM (VM w nazwie programu oznacza maszynę wirtualną), teraz obsługuje także produkty innych producentów, takich jak Sierra Entertainment, Revolution Software i Adventure Soft. ScummVM jest wolnym oprogramowaniem, wydanym na licencji GPL. Za sprawą **Deremona**, ScummVM dla AROSa został uaktualniony do wersji 1.9.0.

![ScummVM](/assets/img/scumm.png)
*ScummVM 1.9.0*

> ## [ResidualVM](http://archives.aros-exec.org/?function=showfile&file=emulation/misc/residualvm-0.3.1-1.i386-aros.zip) (v. 0.3.1)
> (autorzy: Thomas Allen, Torbjorn Andersson i wielu innych)

ResidualVM jest wieloplatformowym interpreterem gier 3D o otwartym kodzie źródłowym, umożliwiającym granie w trójwymiarowe gry przygodowe LucasArts oparte na języku Lua/GrimE: Grim Fandango i Escape from Monkey Island, a także Myst 3 i The Longest Journey. Został on przeniesiony na wiele różnych urządzeń i systemów operacyjnych. 

ResidualVM wykorzystuje OpenGL do sprzętowej akceleracji grafiki 3D. Dołączony jest również programowy renderer dla maszyn bez sprzętowego OpenGL. Ostatnia dostępna wersja ResidualVM została skompilowana dla AROSa przez **Deremona**.

![ResidualVM](/assets/img/residualvm.png)
*ResidualVM*

> ## [ScummVM_Kens](http://archives.aros-exec.org/?function=showfile&file=graphics/icon/scummvm_kens.lha) (v. 0.5)
> ## [ResidualVM-Kens](http://archives.aros-exec.org/?function=showfile&file=graphics/icon/residualvm-kens.lha) (v. 0.5)
> ## [DOSBox Kens](http://archives.aros-exec.org/?function=showfile&file=graphics/icon/dosbox-kens.lha) (v. 0.1)
> ## [MBX Kens](http://archives.aros-exec.org/?function=showfile&file=graphics/icon/mbx-kens-unofficial.lha)(v. 0.1)
> (autor: amiwell79)

Nieoficjalne ikony szuflad w stylu Kens dla ScummVM, ResidualVM, DOSBox oraz gier Myst i MBX.

![Kens](/assets/img/iconscumm.png)
*Zestaw ikon w stylu Kens*

> ## [ADoom3](http://archives.aros-exec.org/?function=showfile&file=game/fps/adoom3-1.5.3.i386-aros.zip) (v. 1.5.3)
> (autor: Nick "Kalamatee" Andrews)

dhewm 3 jest portem źródłowym Doom 3 GPL. Działa na Windows, Linux, macOS, FreeBSD, OpenBSD i AROS, ale powinien działać (lub być łatwo przenośny na każdy system obsługujący OpenGL 1.4 z shaderami ARB, SDL i OpenAL. W porównaniu do oryginalnej wersji Doom3, dhewm3 ma wiele poprawek błędów, obsługuje efekty dźwiękowe podobne do EAX na wszystkich systemach operacyjnych i sprzęcie (poprzez OpenAL Softs EFX), ma znacznie lepszą obsługę rozdzielczości panoramicznych i 64-bitową wsparcie.

Port Doom3 dla AROS-a jest oparty na gałęzi dhewm3 z najnowszej wersji 1.5.3. Skompilowany został przez **Deremona**.

Do uruchomienia potrzebne są oryginalne pliki z danymi z wersji PC. Zakupić ją można na GOGu: https://www.gog.com/pl/game/doom_3

![ADoom3](/assets/img/doom3.jpg)
*ADoom 3*

> ## [MBX Magical Broom Extreme](http://archives.aros-exec.org/?function=showfile&file=game/action/mbx.i386-aros.zip) (v. 1.0)
> (autor: Farox)

Magical Broom Extreme to darmowa horyzontalna strzelanka od japońskiego dewelopera Twin-Tail. Charakteryzuje się trójwymiarowymi efektami broni i całkiem wiągającą rozgrywką. W grze sterujesz czarownicą latającą na miotle. Twoim celem jest przetrwanie podróży do końca etapu. Gra została przeportowana dla AROSa przez **Faroxa**.

![MBX Magical Broom Extreme](/assets/img/mbx.jpg)
*Magical Broom Extreme (MBX)*

> ## [Protrekkr 2](http://archives.aros-exec.org/?function=showfile&file=audio/tracker/protrekkr.i386-aros.zip) (v. 2.6.7)
> (autor: Franck "hitchhikr" Charlet)

ProTrekkr to program typu tracker łączący w sobie syntezator programowy wraz z tradycyjnym trackerem sampli, który może (głównie) być używany do tworzenia muzyki elektronicznej (np. psytrance, trance goa, hard acid, IDM, chip, techno, jungle itp.) do małych intro, dem lub gier. Jest to mocno zmodyfikowana wersja starego NoiseTrekker 2, który został stworzony przez Juana Antonio Arguelles Rius aka Arguru.

Zmiany w najnowszej wersji:
- Naprawiono awarię podczas używania funkcji rand na synth oscs & lfos pod Linuxem
- Dodano procedurę odtwarzania dla PlayStation Vita
- Naprawiono awarię podczas ładowania starszych modułów NoiseTrekker
- Ekran startowy jest teraz opcjonalny

![Protrekkr](/assets/img/protrekkr267.png)
*Protrekkr 2*

> ## [Origami Intro](http://archives.aros-exec.org/?function=showfile&file=demo/intro/origami.i386-aros.zip) (v. 1.0)
> (autor: Faemiyah Demogroup)

Demoscenowe intro Origami zaprezentowane zostało po raz pierwszy na 64kb introcompo na Assembly 2005, gdzie zajęło trzecie miejsce. Wersja dla AROS skompilowana została przez **Faroxa**. Do uruchomienia potrzebujesz karty graficznej z obsługą OpenGL.

![Origami Intro](/assets/img/origami.jpg)
*Origami Intro*

> ## [The Fulcrum](http://archives.aros-exec.org/?function=showfile&file=demo/scene/thefulcrum.i386-aros.zip) (v. 1.0)
> (autorzy: Matrix Demogroup)

Kolejna demoscenowa produkcja przeportowana dla AROSa przez **Faroxa**. The Fulcrum to zwycięskie demo z party Mekka & Symposium 1998. To wydanie dla AROS opiera się na imponującej pracy wykonanej przez M-HT, który przekonwertował wszystkie źródła ASM na
C++/SDL i wydał dla Linuksa i OpenPandora Handheld kilka lat temu. Jego źródła znajdują się tutaj https://github.com/M-HT/fulcrum.

![The Fulcrum](/assets/img/fulcrum.jpg)
*The Fulcrum*

> ## [DUMB](http://archives.aros-exec.org/?function=showfile&file=development/library/libdumb.i386-aros.zip) (v. 0.93)
> (autorzy: Dumb team/M-HT)

DUMB to biblioteka odtwarzaczy IT, XM, S3M i MOD opracowana przez Roberta J. Ohannessiana, Juliena Cugnière'a i Bena Davisa. Dzięki **Faroxowi**, który skompilował ją na potrzeby portu dema Fulcrum, jest teraz dostępna dla wszystkich programistów AROSa do wykorzystania w swoich projektach. 

![DUMB](/assets/img/dumb.png)
*DUMB - "Dynamic Universal Music Bibliotheque"*

> ## [Image2PDF](http://archives.aros-exec.org/?function=showfile&file=office/dtp/image2pdf.lha) (v. 2.6)
> (autor: Bernd Assenmacher)

Małe narzędzie do konwersji obrazów do formatu PDF. Przede wszystkim służy do konwertowania skanów wykonanych np. za pomocą Scandal lub Scanquix do dokumentów PDF w określonych formatach wyjściowych, takich jak A3, A4, A5, Legal, Letter lub ImageSize, ale może być również używane do konwersji innych plików graficznych.

Zmiany w wersji 2.6:
- zaktualizowany plik instrukcji
- W systemach MorphOS i AROS plik instrukcji jest teraz kopiowany do szuflady instalacyjnej.
- W systemie MorphOS polecenie "Path" w s:user-startup jest teraz nieaktywne. Jeśli ma być aktywne, należy je ręcznie odkomentować, zapisać, a następnie zrestartować komputer
- dodano możliwość skalowania obrazów we wszystkich wybranych formatach
- dodano możliwość kompresji dokumentów PDF, gdy zainstalowany jest Ghostscript
- możliwość zmiany orientacji dokumentów PDF (nie w formacie ImageSize)
- można teraz ustawić margines wydruku
- użycie wiersza poleceń automatycznie dostosuje orientację (nie dotyczy formatu ImageSize)
- skompilowano pojedyncze wersje dla obsługiwanych platform
- usunięto aplet z archiwum
- dodano funkcję drukowania dokumentów PDF

![Image2PDF](/assets/img/image2pdf26.png)
*Image2PDF*

> ## [What IFF?](http://archives.aros-exec.org/?function=showfile&file=document/misc/whatiff3.13.nodemo.lha) (v. 3.13)
> (autorzy: A. Vaisey, I. Sorensen, J. Scolieri, K. Saunders, R. O'Malley, T. Paul)

Magazyn o tematyce amigowej wydawany w formacie Amigaguide. Numer 13 - kwiecień 2024.

![What IFF?](/assets/img/whatiff13.png)
*What IFF? - kwiecień 2024*

> ## [High-Low-Equal Poker Card](http://archives.aros-exec.org/?function=showfile&file=game/card/hle-pokercard.lha) (v. 2.10)
> (autor: Juan Carlos Herrán Martín)

Prosta gra karciana. Odgadnij następną kartę, która pojawi się na stole i zdobądź pieniądze oraz punkty. Jest to specjalna wersja promująca inną grę autora  - Los Malditos del Valle del Cerro, która pojawiła się w marcowym podsumowaniu.

Zmiany w wersji 2.10:
- Nowy rozmiar ekranu 800x600 pikseli.
- Skompilowany z ostatnim Hollywood 10.0.
- Środowisko i grafika świata Los Malditos.
- Naprawiono kilka starych błędów.
- Z dwoma ekskluzywnymi taliami z postaciami Los Malditos.

![HLE Poker Card?](/assets/img/hlepoker.jpg)
*High-Low-Equal Poker Card*

> ## [IcarosFix](http://archives.aros-exec.org/?function=showfile&file=development/utility/icaros_2.3_fix.lha) (v. 2.3.4)
> (autorzy: Aros, Third Part Dev)

Icaros to swego czasu najpopularniejsza dystrybucja AROSa. Niestety od kilku lat nieaktualizowana. W tym archiwum znajduje się zestaw poprawek dla Icaros 2.3. W celu instalacji należy nadpisać pliki. Jest to nieoficjalna poprawka.
