# English 90 — Instrukcja obsługi

Minimalistyczna aplikacja webowa (SPA) do 90-dniowej nauki mówionego języka angielskiego i rozumienia ze słuchu. Działa lokalnie w przeglądarce, bez konta i bez abonamentu, z pełnym zapisem postępów w `localStorage`.

---

## 1. Uruchomienie aplikacji

### Na Macu (zalecane — pełne funkcje: mikrofon, ładowanie bloków, powiadomienia)
Otwórz Terminal i wpisz:

```bash
cd ~/Documents/my_english
python3 -m http.server 8080
```

Następnie otwórz w Safari lub Chrome:
**`http://localhost:8080`**

> **Wskazówka:** Samo kliknięcie `index.html` też uruchomi aplikację, ale przeglądarki blokują przy `file://` automatyczne pobieranie plików z folderu `packs/` oraz mikrofon/powiadomienia. Uruchomienie przez `localhost:8080` odblokowuje wszystko.

### Na iPhonie
Masz dwa wygodne sposoby:
- **W domowym Wi-Fi (z Maca):** gdy na Macu działa `python3 -m http.server 8080`, otwórz w Safari na iPhonie adres `http://<nazwa-lub-IP-Maca>:8080` (IP sprawdzisz w *Ustawienia systemowe → Sieć → Wi-Fi*).
- **Lokalnie / przez iCloud / hosting statyczny:** jeśli chcesz korzystać z mikrofonu i trybu offline również poza domem (na spacerze), najwygodniej wystawić folder `my_english` przez darmowy HTTPS (np. GitHub Pages lub Netlify) i w Safari wybrać *Udostępnij → Dodaj do ekranu początkowego*.

---

## 2. Pierwszy start — załadowanie 12 bloków (2000+ pozycji)

Aplikacja ma wbudowany zestaw startowy, a cały 90-dniowy program (**540 fiszek ze zdaniami + 1440 słówek = 1980 dodatkowych pozycji**, razem **2076 pozycji**) leży w folderze `packs/` (`blok-01.json` – `blok-12.json`).

1. Na **Dashboardzie** kliknij **„Załaduj wszystkie 12 bloków (2000+ pozycji)"** (albo wejdź w **Katalog → Mapa 12 bloków tematycznych** i ładuj bloki pojedynczo, tydzień po tygodniu).
2. W polu **„Temat treningu (wyspa tematyczna)"** wybierz:
   - **Wszystkie odblokowane (plan 90 dni)** — domyślny tryb kursu (kolejne miesiące odblokowują się automatycznie co 30 dni, albo wszystkie naraz po włączeniu opcji w *Ustawieniach*),
   - **Konkretny blok 1–12** — np. *1. Wypełniacze i „klej" konwersacyjny*,
   - **⚠️ Trudne / z problemami** — wyłącznie pozycje, które wcześniej sprawiły Ci trudność.

---

## 3. Jak działa system 90 dni i seria z handicapem

- **Cel tygodniowy:** **5 z 7 dni** (Pon–Nd).
- **Handicap (2 dni regeneracji w tygodniu):** możesz opuścić do 2 dni w tygodniu bez utraty serii (`streak`). Dopiero 3. opuszczony dzień w jednym tygodniu zeruje serię.
- **Bonus:** 6. i 7. ukończony dzień w tygodniu oznaczane są gwiazdką ★.
- **Kiedy dzień jest zaliczony?** Po ukończeniu sesji fiszek, pełnej pętli Trybu Spacerowego **lub** sesji 10+ słówek.
- **Przebieg kursu · 90 dni:** na Dashboardzie widzisz 4 liczniki ogólne (zaliczone sesje, dzień kursu, poznane pozycje, dni do końca) oraz wizualną mapę 3 miesięcy (90 kwadracików: zielony = zaliczony, ciemny = dzisiaj, piaskowy = dzień miniony, pusty = przed Tobą).

---

## 4. Pięć trybów nauki

### `01` Trening klasyczny (Fiszki kontekstowe)
- **Przód karty:** naturalne angielskie zdanie z zaznaczonym kluczowym zwrotem + odsłuch lektora (przełącznik prędkości **1.0× / 0.75×**).
- Stuknij w samą kartę (lub naciśnij `Spację`), żeby odkryć tył.
- **Tył karty:**
  - polskie tłumaczenie zdania i krótkie wyjaśnienie zwrotu,
  - **Zadanie mówione:** ułóż własne zdanie na głos i kliknij **🎤 Mów** (wymaga połączenia z internetem do rozpoznawania mowy). Gdy system wykryje użycie zwrotu, pokaże potwierdzenie i (przy włączonym *Auto-przejściu*) po 1,4 s sam zaliczy kartę jako **Dobrze** i przejdzie dalej (możesz kliknąć *Zatrzymaj*, żeby wybrać inną ocenę).
  - **Ocena SRS:** `Nie pamiętam` (wraca za chwilę w tej samej sesji), `Trudne`, `Dobrze`, `Łatwe`.
- **Skróty klawiszowe (Mac):** `Spacja` — sprawdź · `L` — odsłuch · `M` — mikrofon · `1–4` — ocena.

### `02` Słówka EN ⇄ PL (w stylu Duolingo)
- Wybierasz **temat**, **kierunek** (`EN → PL`, `PL → EN` lub `Mieszany`), **tryb** (`Quiz 4 opcje` lub `Fiszki`) oraz liczbę słówek (`10 / 20 / 30`).
- **Auto-przejście:** w quizie po kliknięciu poprawnej odpowiedzi pojawia się komunikat **✓ Dobrze!** i aplikacja sama przechodzi na kolejne pytanie (możesz wyłączyć w ustawieniach lub na ekranie startowym słówek).
- **Fiszki słówek na telefonie:** po odkryciu karty możesz przesuwać palcem (**swipe w prawo = Znam**, **w lewo = Nie znam**) albo użyć przycisków na dole.
- **Skróty klawiszowe:** `1–4` wybór w quizie · `Enter`/`Spacja` dalej/odkryj · `L` odsłuch · `1–3` ocena fiszki.

### `03` Tryb Spacerowy (Hands-Free Audio Loop)
- Zaprojektowany do słuchania w ruchu na słuchawkach (z włączoną blokadą wygaszania ekranu `Screen Wake Lock API`, jeśli przeglądarka ją wspiera).
- **Automatyczna pętla dla każdej karty:**
  1. Lektor czyta angielskie zdanie (`1.0×`).
  2. 2 sekundy pauzy.
  3. Lektor czyta kluczowy zwrot wolniej (`0.8×`) + opcjonalnie polskie znaczenie (`pl-PL`).
  4. Krótki sygnał dźwiękowy i 4 sekundy ciszy na głośne powtórzenie (*shadowing*).
  5. Automatyczne przejście do kolejnej karty.
- Możesz włączyć opcję **„Ukryj tekst (czysty słuch)"** do treningu samego rozumienia ze słuchu.
- *Wskazówka na iPhone:* wyłącz fizyczny przełącznik trybu cichego i nie blokuj ekranu podczas spaceru.

### `04` Powtórki trudne i segregacja według ocen
- Każda karta i słówko zapisuje Twoją ostatnią ocenę (`Nie pamiętam`, `Trudne`, `Dobrze`, `Łatwe`) oraz licznik błędów.
- Na Dashboardzie w sekcji **„Segregacja wg ocen"** widzisz liczbę pozycji w każdej kategorii (kliknięcie kafelka otwiera je w Katalogu).
- Przyciski **„Powtórz trudne fiszki"** i **„Powtórz trudne słówka"** (oraz karta `04 Powtórki trudne`) uruchamiają trening wyłącznie z materiałem, z którym miałeś problemy.

### `05` Egzamin sprawdzający
- **Zakres:** wybierz cały odblokowany materiał, wyłącznie poznane dotąd pozycje, wybrany miesiąc (`1–3`) albo konkretny blok tematyczny (`1–12`).
- **Parametry:** liczba pytań (`10 / 20 / 30`) oraz opcjonalny **timer na pytanie** (`Brak / 15 s / 10 s`).
- **4 typy pytań w jednym teście:**
  1. **Uzupełnianie luki (cloze)** — brakujący zwrot w kontekście zdania.
  2. **Rozumienie ze słuchu** — samo nagranie lektora (bez podglądu angielskiego napisu) i wybór znaczenia.
  3. **Tłumaczenie PL → EN** — wybór spośród 4 opcji.
  4. **Aktywne wpisywanie** — samodzielne wpisanie zwrotu/słówka (ignoruje wielkość liter, znaki interpunkcyjne i opcjonalne `to`).
- **Wynik i nauka na błędach:** próg zdania to **80%**. Po egzaminie widzisz pełną listę błędów z odsłuchem, historię ostatnich podejść, a wszystkie błędne pozycje automatycznie trafiają do **Powtórek trudnych** (z przyciskiem **„Przećwicz błędne pozycje"**).
- **Skróty klawiszowe:** `1–4` wybór opcji · `Enter` zatwierdź / dalej · `L` powtórz odsłuch.

---

## 5. Synchronizacja między Macem a iPhonem

Ponieważ aplikacja działa lokalnie bez chmury, postępy zapisują się osobno na każdym urządzeniu. Aby je połączyć:

1. Na urządzeniu, na którym właśnie ćwiczyłeś, otwórz **Dashboard → ⇄ Synchronizacja (Mac ⇄ iPhone)** (lub **Ustawienia**) i kliknij **„↗ Wyślij stan (AirDrop / iCloud)"**.
   - Wyślij plik `english90-sync.json` AirDropem na drugie urządzenie albo zapisz go w jednym folderze w **iCloud Drive**.
2. Na drugim urządzeniu kliknij **„⇄ Scal z pliku (.json)"** i wskaż ten plik.
3. Aplikacja **nie nadpisze** Twoich postępów — **inteligentnie je scali**: zachowa nowsze oceny SRS dla każdej karty, połączy zaliczone dni w kalendarzu 90 dni, scaloną historię egzaminów oraz dorzuci brakujące bloki i własne słówka.

---

## 6. Przypomnienia i kalendarz (.ics)

Na Dashboardzie w sekcji **⏰ Przypomnienia**:
- ustaw preferowaną godzinę i dni tygodnia (domyślnie Pon–Pt),
- kliknij **„📅 Pobierz przypomnienie do kalendarza (.ics)"** — otwarcie pliku na Macu lub iPhonie doda cykliczne przypomnienie (13 tygodni) prosto do Apple Kalendarza (najbardziej niezawodna opcja na iOS),
- opcjonalnie włącz **Powiadomienia w przeglądarce** (działają, gdy karta z aplikacją jest otwarta).

---

## 7. Katalog / Edytor i własny materiał

W zakładce **Katalog** możesz:
- przeglądać i odsłuchiwać wszystkie zdania oraz słówka,
- filtrować po miesiącu, bloku tematycznym (1–12), statusie i ostatniej ocenie (`Nie pamiętam`, `Trudne`, `Dobrze`, `Łatwe`),
- dodawać własne fiszki i słówka formularzem lub masowo przez **Import JSON** (w zakładce znajduje się gotowy przykład struktury do skopiowania).

---

## 8. Mapa 12 bloków tematycznych (`packs/`)

- **Miesiąc 1 — Fundamenty rozmowy i codzienność:**
  1. `blok-01.json` — Wypełniacze i „klej" konwersacyjny
  2. `blok-02.json` — Codzienna rutyna, dom i nawyki
  3. `blok-03.json` — Relacje, emocje i reakcje
  4. `blok-04.json` — Zakupy, pieniądze i załatwianie spraw
- **Miesiąc 2 — Świat zewnętrzny, praca i działanie:**
  5. `blok-05.json` — Praca, projekty i technologia
  6. `blok-06.json` — Podróże, miasto i przemieszczanie się
  7. `blok-07.json` — Zdrowie, samopoczucie i sport
  8. `blok-08.json` — Czas wolny, hobby i kultura
- **Miesiąc 3 — Opinie, abstrakcja i swobodna dyskusja:**
  9. `blok-09.json` — Wyrażanie opinii i argumentowanie
  10. `blok-10.json` — Przeszłość, wspomnienia i opowiadanie historii
  11. `blok-11.json` — Przyszłość, plany i hipotetyczne sytuacje
  12. `blok-12.json` — Najważniejsze Phrasal Verbs i idiomy
