# English 90

Minimalistyczna aplikacja SPA do 90-dniowej nauki mówionego języka angielskiego i rozumienia ze słuchu. Jeden plik `index.html` + 12 paczek tematycznych w `packs/`, zero zewnętrznych zależności, działa lokalnie i offline.

Szczegółowy przewodnik użytkownika znajdziesz w [INSTRUKCJA.md](INSTRUKCJA.md).

## Uruchomienie

- **Zalecane (Mac — odblokowuje ładowanie paczek `packs/`, mikrofon, powiadomienia i Wake Lock):**

  ```bash
  cd ~/Documents/my_english
  python3 -m http.server 8080
  # otwórz http://localhost:8080
  ```

- **iPhone:** w domowym Wi-Fi otwórz `http://<IP-Maca>:8080` w Safari, albo wystaw folder przez darmowy HTTPS (np. GitHub Pages / Netlify) i wybierz *Udostępnij → Dodaj do ekranu początkowego*.

## Pięć trybów nauki

1. **`01` Trening klasyczny** — fiszki kontekstowe ze zdaniami (`**zwrot**`), odsłuchem TTS (`1.0× / 0.75×`), zadaniem mówionym z rozpoznawaniem mowy (`SpeechRecognition`) oraz oceną SRS.
2. **`02` Słówka EN ⇄ PL** — szybki Quiz (4 opcje z auto-przejściem) oraz Fiszki z gestami przesuwania na telefonie; kierunek `EN → PL`, `PL → EN` lub mieszany.
3. **`03` Tryb Spacerowy** — automatyczna pętla audio hands-free (zdanie `1.0×` → pauza → zwrot `0.8×` → opcjonalnie PL → sygnał i 4 s na *shadowing*) z `Screen Wake Lock API` i trybem ukrytego tekstu.
4. **`04` Powtórki trudne** — segregacja wszystkich kart i słówek według ostatniej oceny (`Nie pamiętam`, `Trudne`, `Dobrze`, `Łatwe`) i szybki powrót do problematycznego materiału.
5. **`05` Egzamin sprawdzający** — mieszany test (uzupełnianie luk w zdaniach, rozumienie ze słuchu, tłumaczenie PL → EN i aktywne wpisywanie) z wybranego zakresu (`10 / 20 / 30` pytań, opcjonalny timer `15 s / 10 s`, próg zdania `80%`). Błędy automatycznie trafiają do **Powtórek trudnych**.

## Dane, paczki i synchronizacja

- **Baza materiału (2076 pozycji):** 96 pozycji wbudowanych (36 kart + 60 słówek) + 12 paczek w `packs/blok-01.json` … `blok-12.json` (łącznie 540 kart + 1440 słówek = 1980 dodatkowych pozycji), ładowanych jednym kliknięciem z Dashboardu lub Katalogu.
- **Zapis lokalny:** wszystko w `localStorage` pod kluczem `english90.v1` (postępy SRS, kalendarz 90 dni, historia egzaminów, ustawienia, własne karty i słówka).
- **Synchronizacja Mac ⇄ iPhone:** przycisk *Wyślij stan (AirDrop / iCloud)* eksportuje `english90-sync.json`, a *Scal z pliku (.json)* inteligentnie łączy postępy z obu urządzeń (nowsze oceny SRS, suma zaliczonych dni, historia egzaminów, własny materiał) bez nadpisywania danych.
- **Przypomnienia:** eksport cyklicznego wydarzenia `.ics` do Apple Kalendarza + opcjonalne powiadomienia przeglądarkowe.

## Format własnych kart i słówek (Import JSON)

Karta kontekstowa:

```json
{
  "id": "opcjonalne",
  "month": 1,
  "topic": 1,
  "en": "I'm **looking forward to** the weekend.",
  "pl": "Nie mogę się doczekać weekendu.",
  "phrasePl": "nie mogę się doczekać",
  "note": "Wyjaśnienie zwrotu",
  "prompt": "Zadanie mówione"
}
```

Słówko:

```json
[{ "kind": "word", "month": 1, "topic": 1, "en": "reliable", "pl": "niezawodny" }]
```

## Zasady planu 90 dni

- **Cel tygodniowy:** `5 z 7` dni (Pon–Nd) z **handicapem 2 dni** — do 2 opuszczonych dni w tygodniu nie zrywa serii; dopiero 3. opuszczony dzień ją zeruje. Dni 6. i 7. oznaczane są jako bonus ★.
- **Przebieg kursu:** na Dashboardzie dostępny jest przegląd całego 90-dniowego planu (4 liczniki ogólne + wizualna siatka 3 miesięcy × 30 dni).
- **Zaliczenie dnia:** ukończenie sesji fiszek, pełnej pętli Trybu Spacerowego **lub** sesji słówek (10+).
- **SRS:** uproszczony SM-2 (`Nie pamiętam` / `Trudne` / `Dobrze` / `Łatwe`); `Nie pamiętam` wraca jeszcze w tej samej sesji.
