---
layout: post
title: Jak zmienić Język Systemu
subtitle: w AROS ABIv11 64-bit
lang: pl
ref: tutL
---

{: .box-success}
Pokażę kroki na przykładzie języka polskiego. W przypadku innych języków postępowanie jest analogiczne. Należy jedynie mieć na uwadze, aby wybierać stronę kodową odpowiednią dla swojego języka oraz używać czcionek, które posiadają w sobie znaki diaktryczne odpowiednie dla wybranego języka.

## Krok 1: FTManager i instalacja czcionek

**FreeType Font Manager** pozwala nam zainstalować w systemie czcionki True Type z odpowiednią stroną kodową. W przypadku języka polskiego będzie to *ISO-8859-2*, gdyż takiej strony kodowej używa polska lokalizacja. Wraz z ABIv11 64-bit otrzymujemy zestaw czcionek True Type zlokalizowanych w *AROS:Fonts/TrueType/*.

![TrueType](/assets/img/lang3.jpg)

Nie wszystkie z tych czcionek mają w sobie polskie znaki diaktryczne. Jedynymi, które je posiadają są: Barlow, Bellefair, Carbon, GoodTimes, Pakenham, Spectral, WorkSans. Nie każda z nich będzie prezentowała się dobrze jako czcionka systemowa. Tak naprawdę powinniśmy rozważać jedynie wybór pomiędzy Barlow lub WorkSans.

Niezłym pomysłem będzie znalezienie odpowiedniej czcionki True Type w internecie lub wykorzystanie jakiejś czcionki z Windows jeśli jesteśmy użytkownikiem tego systemu. Pamiętajmy tylko, aby była to czcionka, która ma wbudowane znaki diaktryczne dla naszego języka. Ja zdecydowałem się wykorzystać czcionkę Segoe UI Variable z Windows 11. W tym celu przerzuciłem za pomocą pendrive plik SegUIVar.tff z *C:/Windows/Fonts/* do *AROS:Fonts/TrueType/*.

![SegUIVar](/assets/img/lang4.jpg)

Teraz możemy przejść do *AROS:System/FTManager*.

W polu **Codepage** wybieramy *ISO-8859-2* dla języka polskiego. Następnie wyszukujemy w oknie nazwę czcionki, którą chcemy zainstalować z wybraną stroną kodową (w naszym wypadku Segoe UI Variable) i klikamy dwukrotnie na jej nazwę.

![Codepage](/assets/img/lang5.jpg)

Otworzy nam się nowe okno z parametrami czcionki. W polu **Name** możemy w tym miejscu zmienić nazwę czcionki pod jaką będzie widoczna w systemie (możemy np. dodać na końcu nazwy "PL", aby podkreślić, że jest to czcionka z polskimi znakami). Na koniec klikamy *"Install"*. Pozornie nic się nie dzieje, ale po tej operacji w katalogu *AROS:Fonts/* pojawią się dwa nowe pliki z nazwą naszej czcionki i rozszerzeniami .font oraz .otag. W tym momencie czcionka jest zainstalowana w systemie. Możemy zamknąć okno i przejść do kolejnego kroku. 

![Install](/assets/img/lang6.jpg)

{: .box-success}
Jeżeli potrzebujemy czcionek **bitmapowych**, najlepiej ściągnąć gotową paczkę z Aminetu. W przypadku polskich czcionek można ściągnąć ten plik:
[http://aminet.net/text/bfont/CzcionkiISO.lha](http://aminet.net/text/bfont/CzcionkiISO.lha)  
Zawiera zestaw czterech krojów polskich czcionek bitmapowych w standardzie kodowania ISO-8859-2. Zawartość należy rozpakować do katalogu *AROS:Fonts/*

## Krok 2: Input i Locale.

Kierujemy się do *AROS:Prefs/Input* gdzie zmienimy mapowanie klawiatury na przystosowane do naszego języka. Na liście **Keyboards** klikamy dwukrotnie na *"Polski"*. W polu **Default** pojawi nam się polska flaga. Klikamy w zlokalizowany obok niego przycisk *"Set"*, aby zatwierdzić swój wybór. Na koniec klikamy przycisk *"Save"*.

![Input](/assets/img/lang1.jpg)

Przechodzimy do *AROS:Prefs/Locale*. W **Region** wybieramy *"Polska"*, a w **Preferred Language** *"Polski"*. W polu **Default character set** wybieramy *ISO-8859-2*, gdyż takiej strony kodowej używa polska lokalizacja w ABiv11 64-bit. Jeśli mamy ustawione wszystko jak na poniższym screenie naciskamy *"Save"*.

![Locale](/assets/img/lang2.jpg)

## Krok 3: Ustawienie czcionek w systemie

Jeśli mamy zainstalowaną jedną lub więcej czcionek z polskimi znakami możemy teraz przejść do *AROS:Prefs/Fonts* i je wybrać. Mamy możliwość ustawienia różnych czcionek i/lub rozmiarów. Klikamy *"Save"* i przechodzimy do *AROS:Prefs/Zune*. Tutaj czcionki zmieniamy w zakładkach **"Windows"** oraz **"Groups"**. Po zapisaniu zmian resetujemy komputer i nasza podstawowa zmiana języka jest gotowa.

![Fonts](/assets/img/lang7.jpg)

![FontsPref](/assets/img/lang8.jpg)

![ZunePref](/assets/img/lang9.jpg)
