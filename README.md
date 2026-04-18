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

### Losowanie
- Konfigurowalna liczba losowanych uczniów naraz (1, 2, 3 lub więcej)
- Losowanie **bez powtórzeń** — każdy numer pojawia się tylko raz aż do wyczerpania całej puli
- Elastyczne losowanie — gdy w puli zostaje mniej uczniów niż ustawiona liczba, program nadal pozwala losować (brakujące pola wypełniane są „-")
- Wylosowane numery oznaczone złotym kolorem ✓ na siatce
- Cofanie ostatniego losowania (przycisk ↩️)
- Gdy pula się wyczerpie — przycisk „🔄 Resetuj kolejkę" rozpoczyna nową rundę

### Historia
- Każde losowanie zapisywane jest z datą
- Historia wyświetlana w tabeli dla każdej klasy osobno
- Dzisiejszy wpis oznaczony etykietą „dziś"

### Statystyki
- Podgląd najczęściej i najrzadziej losowanych uczniów dla każdej klasy
- Wykres aktywności losowań w czasie

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

## 🔒 Prywatność

Wszystkie dane (klasy, pule numerów, historia losowań, nieobecności) przechowywane są **wyłącznie lokalnie** w przeglądarce urządzenia (`localStorage`). Żadne dane nie są wysyłane na żaden serwer. Aplikacja nie używa plików cookie ani narzędzi analitycznych.

---

## 🛠️ Technologie

- Vanilla HTML / CSS / JavaScript — zero zewnętrznych zależności
- PWA (Progressive Web App) z Service Workerem (`sw.js`) i manifestem (`manifest.json`) — działa offline
- localStorage do trwałego przechowywania danych

---

## 📄 Licencja

© 2025–2026 Krzysztof Jureczek · Wszelkie prawa zastrzeżone.  
Szczegóły w pliku [LICENSE](LICENSE) oraz [REGULAMIN](REGULAMIN.md).
