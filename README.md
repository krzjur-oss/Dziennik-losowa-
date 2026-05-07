# 📒 Dziennik Losowań

Aplikacja PWA do losowania numerów uczniów z dziennika klasowego. Działa w przeglądarce na tablecie i telefonie z Androidem — bez instalacji, w pełni offline.

## 🚀 Uruchom aplikację

👉 **[https://krzjur-oss.github.io/Dziennik-losowa-/](https://krzjur-oss.github.io/Dziennik-losowa-/)**

---

## ✨ Funkcje

### Klasy i pule
- Dowolna liczba klas z osobnymi, niezależnymi ustawieniami
- Konfigurowalny zakres numerów (1–N) dla każdej klasy osobno
- Możliwość wykluczenia numerów uczniów nieuczęszczających na zajęcia
- Tryb nieobecności — tymczasowe wykluczenie uczniów z losowania bez usuwania ich z puli
- **Przycisk „✅ Wszyscy wrócili"** — usuwa nieobecność wszystkich uczniów jednym kliknięciem (pojawia się gdy ktoś jest oznaczony jako nieobecny)
- **🆕 Zgłaszanie się do odpowiedzi** — podwójne kliknięcie oznacza ucznia który sam się zgłosił (nie będzie losowany)
- **Przycisk „🙋 Wyczyść zgłoszonych"** — usuwa oznaczenie wszystkich zgłoszonych jednym kliknięciem

### Losowanie
- Konfigurowalna liczba losowanych uczniów naraz (1, 2, 3 lub więcej)
- Losowanie **bez powtórzeń** — każdy numer pojawia się tylko raz aż do wyczerpania całej puli
- **Automatyczne wykluczenie zgłoszonych** — uczniowie którzy sami się zgłosili nie biorą udziału w losowaniu
- Elastyczne losowanie — gdy w puli zostaje mniej uczniów niż ustawiona liczba, program nadal pozwala losować (brakujące pola wypełniane są „-")
- Wylosowane numery oznaczone złotym kolorem ✓ na siatce
- Cofanie ostatniego losowania (przycisk ↩️)
- Gdy pula się wyczerpie — przycisk „🔄 Resetuj kolejkę" rozpoczyna nową rundę

### Oznaczanie uczniów
Każdy numer może mieć jeden z pięciu stanów:

| Stan | Kolor | Emoji | Obsługa | Czy losowany? |
|------|-------|-------|---------|---------------|
| **Aktywny** | 🟢 Zielony | — | Pojedyncze kliknięcie (włącz/wyłącz) | ✅ Tak |
| **Zgłosił się** | 🔵 Niebieski | ✋ | Podwójne kliknięcie | ❌ Nie |
| **Nieobecny** | 🔴 Czerwony | ⊘ | Prawy przycisk / długie przytrzymanie | ❌ Nie |
| **Wylosowany** | 🟡 Złoty | — | Automatycznie po losowaniu | ❌ Nie (dziś) |
| **Wykluczony** | ⚫ Szary | — | Pojedyncze kliknięcie (wyłącz) | ❌ Nie |

**Obsługa na różnych urządzeniach:**
- **Desktop:** pojedyncze LPM (włącz/wyłącz), podwójne LPM (zgłoszony), prawy przycisk (nieobecny)
- **Mobile:** pojedyncze dotknięcie (włącz/wyłącz), podwójne dotknięcie (zgłoszony), długie przytrzymanie (nieobecny)

### Historia
- Każde losowanie zapisywane jest z datą
- Historia wyświetlana w tabeli dla każdej klasy osobno
- Dzisiejszy wpis oznaczony etykietą „dziś"

### Statystyki
- Podgląd najczęściej i najrzadziej losowanych uczniów dla każdej klasy
- Wykres aktywności losowań w czasie
- Licznik zgłoszonych uczniów widoczny w statystykach puli

### Zarządzanie klasami
- Usuwanie pojedynczej klasy przez najechanie na zakładkę i kliknięcie ✕
- Długie naciśnięcie (touch) na tablecie odkrywa przycisk usuwania
- Panel „🗂 Klasy" umożliwia usunięcie wybranych lub wszystkich klas jednocześnie
- Duplikowanie klasy — skopiuj konfigurację do nowej klasy

### Kopia zapasowa
- **💾 Eksport** — pobiera plik JSON ze wszystkimi danymi
- **📂 Import** — wczytuje wcześniej zapisany plik JSON i przywraca wszystkie dane
- Automatyczna kopia zapasowa w localStorage

### Interfejs
- **☰ Hamburger menu** — wszystkie opcje nagłówka (Pomoc, Klasy, Eksport, Import, O aplikacji) zebrane w jednym miejscu
- **⚙️ Zwijane menu „Akcje klasy"** — przyciski selekcji, ustawień, duplikowania i statystyk schowane w rozwijanym panelu
- **🌙 Tryb ciemny** — przełącznik w hamburger menu; wybór zapamiętywany między sesjami, automatyczne wykrywanie systemowego motywu
- Modal **ℹ️ O aplikacji** z zakładkami README, Aktualizacje, Regulamin i Licencja — w pełni scrollowalny na urządzeniach mobilnych

### Pomoc
- Interaktywny samouczek krok po kroku uruchamia się automatycznie przy pierwszym użyciu
- Przycisk **❓ Pomoc** w menu otwiera instrukcję w dowolnym momencie
- Historia zmian dostępna w zakładce **🆕 Aktualizacje** w „O aplikacji"

---

## 📱 Instalacja na Androidzie (PWA)

1. Otwórz **Chrome** na tablecie lub telefonie
2. Wejdź na: **[https://krzjur-oss.github.io/Dziennik-losowa-/](https://krzjur-oss.github.io/Dziennik-losowa-/)**
3. Naciśnij menu **⋮** → **„Dodaj do ekranu głównego"**
4. Potwierdź — ikona pojawi się jak normalna aplikacja
5. Od tej chwili działa **offline**, bez paska przeglądarki

> **Wskazówka:** Dane aplikacji zainstalowanej jako PWA są przechowywane oddzielnie od danych przeglądarki — czyszczenie historii Chrome nie usuwa danych klas i losowań.

---

## 🎯 Przykład użycia — Lekcja matematyki

**Scenariusz:** Klasa 2a, 30 uczniów, chcesz wylosować 2 osoby do odpowiedzi przy tablicy.

1. **Start lekcji:**
   - Oznacz 2 nieobecnych (nr 7, 15) — długie przytrzymanie lub prawy przycisk
   
2. **Pytanie do klasy:** „Kto zna odpowiedź?"
   - 3 uczniów zgłasza się (nr 5, 12, 22)
   - Podwójnie klikasz ich numery — stają się niebieskie z emoji ✋
   
3. **Losowanie:**
   - Klikasz „🎲 Losuj" — program losuje spośród 25 uczniów (30 - 2 nieobecni - 3 zgłoszeni)
   - Wylosowani: np. nr 18 i 24
   
4. **Kolejne pytanie:**
   - Znów kilka osób się zgłasza — oznaczasz je podwójnym kliknięciem
   - Losujesz kolejne osoby
   
5. **Koniec lekcji:**
   - Klikasz „✅ Wszyscy wrócili" — czyści nieobecnych
   - Klikasz „🙋 Wyczyść zgłoszonych (7)" — wszyscy wracają do puli
   - Gotowe na następną lekcję!

---

## 🔒 Prywatność

Wszystkie dane (klasy, pule numerów, historia losowań, nieobecności, zgłoszenia) przechowywane są **wyłącznie lokalnie** w przeglądarce urządzenia (`localStorage`). Żadne dane nie są wysyłane na żaden serwer. Aplikacja nie używa plików cookie ani narzędzi analitycznych.

---

## 🛠️ Technologie

- Vanilla HTML / CSS / JavaScript — zero zewnętrznych zależności
- PWA (Progressive Web App) z Service Workerem (`sw.js`) i manifestem (`manifest.json`) — działa offline
- localStorage do trwałego przechowywania danych

---

## 📋 Historia wersji

### v2.0 (2026-05-07) — Zgłaszanie się do odpowiedzi
- ✋ Oznaczanie uczniów którzy sami się zgłosili (podwójne kliknięcie)
- 🔵 Wizualne wyróżnienie zgłoszonych (niebieski kolor, emoji ✋)
- 🚫 Automatyczne wykluczenie zgłoszonych z losowania
- 📊 Licznik zgłoszonych w statystykach puli
- 🙋 Przycisk „Wyczyść zgłoszonych" w menu akcji klasy
- 🔄 Auto-czyszczenie przy resetowaniu puli (Odznacz wszystkie, Parzyste, Nieparzyste)

### v1.9 (2026-04-17) — Kompaktowy interfejs
- ☰ Hamburger menu — wszystkie opcje nagłówka w jednym miejscu
- ⚙️ Zwijane menu „Akcje klasy" dla oszczędności miejsca
- 📱 Lepsze dostosowanie do małych ekranów

### v1.6–1.8
- ℹ️ Modal „O aplikacji" z zakładkami
- ✅ Przycisk „Wszyscy wrócili"
- 🎯 Elastyczne losowanie przy nieparzystej liczbie uczniów
- 📊 Statystyki i duplikowanie klas
- 🌙 Tryb ciemny

### v1.0 (2026-03-30) — Wersja początkowa
- 🎲 Podstawowe losowanie bez powtórzeń
- 📝 Historia losowań
- 💾 Eksport/Import danych
- 📱 PWA — tryb offline

---

## 📄 Licencja

© 2025–2026 Krzysztof Jureczek · Wszelkie prawa zastrzeżone.  
Szczegóły w pliku [LICENSE](LICENSE) oraz [REGULAMIN](REGULAMIN.md).
