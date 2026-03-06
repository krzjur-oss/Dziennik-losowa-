# 📒 Dziennik Losowania

Aplikacja PWA do losowania numerów uczniów z dziennika klasowego. Działa w przeglądarce na tablecie i telefonie z Androidem — bez instalacji, w pełni offline.

## 🚀 Uruchom aplikację

👉 **[https://krzjur-oss.github.io/Dziennik-losowa-/](https://krzjur-oss.github.io/Dziennik-losowa-/)**

---

## ✨ Funkcje

### Klasy i pule
- Dowolna liczba klas z osobnymi, niezależnymi ustawieniami
- Numery od 1 do 30 dla każdej klasy osobno
- Możliwość wykluczenia numerów uczniów nieobecnych lub nieuczęszczających na zajęcia
- Przyciski „Zaznacz wszystkie" / „Odznacz wszystkie"

### Losowanie
- Wybór trybu losowania przy tworzeniu klasy: **1, 2 lub 3 numery** jednorazowo
- Losowanie **bez powtórzeń** — każdy numer pojawia się tylko raz aż do wyczerpania całej puli
- Wylosowane numery oznaczone złotym kolorem ✓ na siatce
- Gdy pula się wyczerpie — przycisk „Resetuj kolejkę" rozpoczyna nową rundę
- Obsługa nieparzystej liczby uczniów — ostatnie losowanie wyciąga tyle numerów ile zostało

### Historia
- Każde losowanie zapisywane jest z datą
- Historia wyświetlana w tabeli dla każdej klasy osobno
- Dzisiejszy wpis oznaczony etykietą „dziś"

### Zarządzanie klasami
- Usuwanie pojedynczej klasy przez przytrzymanie zakładki (długie naciśnięcie)
- Panel „🗂 Klasy" umożliwia usunięcie wybranych lub wszystkich klas jednocześnie

### Kopia zapasowa
- **💾 Eksport** — generuje kod JSON ze wszystkimi danymi; można go zapisać w Notatniku
- **📂 Import** — wczytuje wcześniej zapisany eksport i przywraca wszystkie dane
- Zabezpiecza przed utratą danych przy czyszczeniu przeglądarki

### Samouczek
- Interaktywny samouczek krok po kroku uruchamia się automatycznie przy pierwszym użyciu
- Przycisk „Pomiń samouczek" dla użytkowników zaznajomionych z aplikacją
- Przycisk **❓ Pomoc** w nagłówku uruchamia samouczek ponownie w dowolnym momencie

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

Wszystkie dane (klasy, pule numerów, historia losowań) przechowywane są **wyłącznie lokalnie** w przeglądarce urządzenia. Żadne dane nie są wysyłane na żaden serwer.

---

## 🛠️ Technologie

- Vanilla HTML / CSS / JavaScript — zero zewnętrznych zależności
- PWA (Progressive Web App) z Service Workerem — działa offline
- localStorage do trwałego przechowywania danych
