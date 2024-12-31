---
layout: post
title: Podsumowanie roku 2024
subtitle: AROS x86
lang: pl
ref: 1224
---

Koniec roku to czas refleksji i podsumowań. Po latach mniejszej aktywności, możemy śmiało powiedzieć, że ten rok przyniósł nam wiele pozytywnych wydarzeń. Z miesiąca na miesiąc obserwowaliśmy znaczący postęp, który mieliście okazję śledzić na naszym blogu. AROS ruszył naprzód z impetem i nie zamierza zwalniać tempa!


### System

W samym core systemu działo się chyba najwięcej. Główne dystrybucje bazują obecnie na 32-bitowej gałęzi **Deadwooda** (ABIv0), a ta miała w tym roku jedno główne wydanie (ABIv0 20220318-1) i dwie duże aktualizacje zbiorcze z poprawkami.

Deadwood wydał także wersję 64-bitową systemu (ABIv11) w wersji linux hosted (ABIv11 20241102-1) oraz AxRuntime w wersji 41.12, co zapowiada w niedługim czasie całkowitą przesiadkę na 64-bity. Opracował też prototyp emulatora, który umożliwi na 64-bitowym AROSie uruchamianie programów napisanych dla 32-bitowej wersji systemu. 

Uruchomienie przez Deadwooda takich inicjatyw jak *"Irytujący Bug Miesiąca"* pozwoliło zbliżyć deweloperów z użytkownikami i skupić się na naprawie błędów, których społeczność oczekiwała najbardziej. To był pracowity i owocny rok w jego wykonaniu.

Chociaż obecnie postęp w większości jest na barkach Deadwooda, to warto odnotować, że nie byłby on tak szybki bez wcześniejszej pracy włożonej w rozwój AROSa przez **Kalamatee** i innych deweloperów. Bardzo liczymy na ich powrót do aktywnej pracy nad systemem!


### Dystrybucje

Mieliśmy w 2024 roku dwie aktualizowane dystrybucje dla architektury **x86**.

**AROS One** wydawany przez **AMIGASYSTEM** to najbardziej kompletna dystrybucja AROSa. Dostaliśmy w tym roku kilka wydań, zawsze po większej aktualizacji bazowego systemu. W AROS One jest pod ręką wszystko czego możemy tylko potrzebować. Mnóstwo programów i gier, wiele gotowych konfiguracji i skryptów. Distro jest bardzo spójne pod względem wyglądu i ikon, posiada też wiele dodatkowych skórek i tapet, więc możemy je dostosować pod siebie. Najnowszym wydaniem jest wersja 2.7.

Drugą dystrybucją jest **Tiny AROS**, której autorem jest **Amiwell79**. Jak sama nazwa wskazuje to distro jest przeznaczone dla minimalistów, którzy nie potrzebują wszystkiego, ale jednak woleliby nie zaczynać od gołego systemu. Najlepiej wypróbować każdą i wybrać tę, która będzie nam bardziej pasowała.

Obie dystrybucje używają obecnie Wanderera jako domyślnego pulpitu.

**Olaf Schönweiß** wprawdzie nie wydał nowej wersji **AROS Vision** w 2024 roku, ale intensywnie pracował nad kolejną wersją swojej dystrybucji dla architektury **m68k**. Możemy oczekiwać, że nowe wydanie ukaże się na początku 2025 roku.

### Sprzęt

Lista rekomendowanego sprzętu dla AROSa wzbogaciła się o dwie płyty główne: **ASUS P8Z68-V LX** oraz **Gigabyte GA-MA770T UD3/UD3P**. Moim zdaniem warto przyjrzeć się konstrukcji ASUSa. Na tę chwilę jest to najnowszy i najmocniejszy sprzęt z listy rekomendowanych, niedrogi i szeroko dostępny w serwisach aukcyjnych. Jeśli planujesz zakup sprzętu pod AROSa będzie to najlepszy wybór. Rekomendowane płyty mają zapewnione długoterminowe wsparcie, wszystkie nowe wydania AROSa będą testowane pod względem kompatybilności z nimi.

Do sprzedaży trafił **A600GS**. Na sprzęcie zainstalowany jest system Amibench, który wykorzystuje wersję AROSa m68k.

### Dla programistów

Hollywood cieszy się niesłabnącą popularnością wśród twórców oprogramowania dla Amigi NG. w 2024 na AROSa wyszedł **Hollywood Designer 7.0** - nakładka wspomagająca tworzenie prezentacji, gier i aplikacji. Od wydania poprzedniej wersji minęły dwa lata i przez ten czas autor wprowadził wiele ulepszeń. Program do działania wymaga pakietu Hollywood w wersji 10.0. Zarówno Hollywood jak i Hollywood Designer są oprogramowaniem komercyjnym.

Dzięki **Serk118** otrzymaliśmy biblioteki **GLFW 3.4** i **Raylib 5.0**. GLFW umożliwia tworzenie aplikacji OpenGL i OpenGL ES. Zapewnia proste, niezależne od platformy API do tworzenia okien, kontekstów i powierzchni, odczytu danych wejściowych, obsługi zdarzeń itp. Z kolei Raylib to prosta i łatwa w użyciu biblioteka do programowania gier wideo wykorzystująca GLFW. Otwiera to nowe pole do portowania i tworzenia oprogramowania dla AROS.

**Deremon** przygotował długo wyczekiwaną aktualizację **Pythona**. W najnowszych dystrybucjach i w AROS Archives mamy już wersję **3.3.7**.

**Farox** przeportował i udostępnił bibliotekę muzyczną **DUMB** ("Dynamic Universal Music Bibliotheque"), którą wykorzystał przy portowaniu wielu demoscenowych produkcji dla AROSa.

Kompilator **GCC** został zaktualizowany do wersji **10.5.0**. Dzięki ciężkiej pracy **ThatGuyWithTheKids** mamy teraz zaktualizowaną wersję GCC na gałęzi głównej, zarówno dla x86_64, jak i m68k.


### Programy i internet

Wydarzeniem 2024 roku na pewno jest wydanie przez Deadwooda przeglądarki **Odyssey 2.1**. Silnik Webkit został zaktualizowany od sierpnia 2015 r. do lutego 2019 r. W rezultacie Youtube, a także wiele innych nowoczesnych witryn ponownie działa w przeglądarce AROSa. Dodatkowo, przeportowany został media player z przeglądarki Wayfarer 1.21 oraz włączona akceleracja dekodowania oparta o instrukcje SSE. Wydane zostały też wersje 64-bitowe Odyssey Web Browser dla AROS hosted i AxRuntime oferujące znacznie większą wydajność dzięki akceleracji JavaScript za pomocą kompilatora JIT.

Kolejną głośną premierą był **Final Writer 7.1**. Jest to bez wątpienia najbardziej rozbudowany i najlepszy edytor tekstu w naszym amigowym świecie. Final Writer jest programem komercyjnym, ale wart jest każdego wydanego na niego dolara. Za darmo ze strony autora można pobrać wersję demonstracyjną programu.

**Steffen Gutman** wypuścił **BeeBase** w wersji **1.1**. Jest to relacyjny, programowalny system baz danych z graficznym interfejsem użytkownika.

**jPV** wydał **RNOEffects 2.0**. Jest to program do przetwarzania obrazów z naciskiem na dobre opcje konwersji wsadowej, efekty oparte na kanale alfa i edycję pikseli. Program został napisany w Hollywood i jednocześnie jest świetnym przykładem jak wiele można w nim osiągnąć.

Duet Farox i Deremon przeportowali dla AROSa **Fast Tracker 2** - legendarny demoscenowy tracker, którego główną innowacją było wprowadzenie formatu plików XM (Extended Module). Ponadto w tym roku **Franck "hitchhikr" Charlet** wydał kilka aktualizacji swojego regularnie rozwijanego trackera **Protrekkr**.

Mijający rok przyniósł nam też AROSowe wersje doskonale znanych z Amigi klasycznej programów **World Construction Set** oraz **Bars & Pipes**.


### Gry

Nie mogło też zabraknąć gier. **Farox** przygotował nam port **wipEout Rewrite**. Kultowe futurystyczne wyścigi z PSX'a zawitały wreszcie na AROSa. Gra jest naprawdę solidna, a dzięki wysokiej rozdzielczości gra się lepiej niż w oryginale. Innym ciekawym portem od Faroxa jest **Magical Broom Extreme**. Mamy tu do czynienia z grą typu shoot 'em-up. W grze sterujemy czarownicą latającą na miotle. Towarzyszy nam ładna grafika 3D, a na ekranie dzieje się naprawdę wiele.

Kolejny duży tytuł to aktualizacja **Doom 3** przeportowanego pierwotnie przez **Kalamatee**. Gry oczywiście nie trzeba nikomu przedstawiać. W tym roku dzięki Deremonowi silnik dhewm3, na którym opiera się gra, został zaktualizowany do wersji 1.5.3. Ponadto **Deremon** zaktualizował emulatory ScummVM do wersji 1.9.0-1, ResidualVM do wersji 0.3.1-1 oraz GemRB do wersji 0.8.8-0. Fani przygodówek mają powody do radości, bo dzięki tym aktualizacjom mamy wiele nowych gier, które są możliwe do ogrania na AROSie.

Pojawiło się kilkadziesiąt mniejszych gier, bądź aktualizacji, których nie sposób teraz wszystkich wymienić. Po szczegóły odsyłam do wcześniejszych comiesięcznych podsumowań. Dziękuję autorom takim jak Domenico Lattanzi, Giovanni Iacobelli, Juan Carlos Herran Martin i innym za ich nieustające wsparcie dla AROSa.

Także wydawane w tym roku produkcje na Amigę klasyczną w większości przypadków bez problemu mogliśmy odpalić na AROSie przy pomocy Janus-UAE.

### Podsumowanie

Rok 2024 okazał się wyjątkowo pomyślny dla użytkowników AROSa. Z nadzieją patrzymy w przyszłość, ponieważ nadchodzący rok zapowiada się jeszcze lepiej. Osobiście życzyłbym sobie żebyśmy mieli jeszcze więcej aktywnych deweloperów i liczę, że tak właśnie się stanie. Przesiadka na 64-bitowy natywny system stanowi świetną okazję do powrotu i dalszego rozwoju.
