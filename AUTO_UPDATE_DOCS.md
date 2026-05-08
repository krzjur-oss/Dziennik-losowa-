# 🔄 Mechanizm automatycznej aktualizacji w Dziennik Losowania v2.0

## 🎯 Problem

**Przed zmianami:** Użytkownicy musieli ręcznie czyścić cache przeglądarki aby zobaczyć nowe wersje aplikacji. Service Worker cache'ował starą wersję i nie aktualizował się automatycznie.

**Po zmianach:** Aplikacja wykrywa aktualizacje automatycznie i informuje użytkownika przyjaznym powiadomieniem. Użytkownik może zaktualizować jednym kliknięciem bez tracenia danych.

---

## ✨ Funkcje mechanizmu auto-update

### 1. **Wykrywanie aktualizacji Service Workera**
```javascript
reg.addEventListener('updatefound', () => {
  // Nowa wersja SW została znaleziona
  // Pokaż powiadomienie użytkownikowi
});
```

### 2. **Okresowe sprawdzanie aktualizacji**
```javascript
setInterval(() => {
  reg.update(); // Sprawdź co 60 sekund
}, 60000);
```

### 3. **Wykrywanie aktualizacji przez wersję localStorage**
```javascript
const storedVersion = localStorage.getItem('appVersion');
if (storedVersion !== CURRENT_VERSION) {
  // Wykryto aktualizację - wyczyść stary cache
  // Pokaż powiadomienie o nowej wersji
}
```

### 4. **Automatyczne przeładowanie po aktualizacji**
```javascript
navigator.serviceWorker.addEventListener('controllerchange', () => {
  window.location.reload(); // Nowy SW przejął kontrolę
});
```

### 5. **Przyjazne powiadomienie dla użytkownika**
- Wyświetla się na dole ekranu
- Jasna wiadomość: "🎉 Nowa wersja aplikacji jest dostępna!"
- Przycisk "Aktualizuj" - jeden klik i gotowe
- Automatycznie znika po 10 sekundach

### 6. **Ręczne wymuszenie sprawdzenia aktualizacji**
- Przycisk "🔄 Sprawdź aktualizacje" w modalu "O aplikacji"
- Natychmiastowe sprawdzenie bez czekania na automatyczny timer

---

## 🔧 Jak to działa?

### Krok 1: Service Worker wykrywa nową wersję
```
Użytkownik otwiera aplikację
     ↓
SW sprawdza czy sw.js się zmienił
     ↓
Jeśli TAK: updatefound event
     ↓
Nowy SW rozpoczyna instalację
```

### Krok 2: Powiadomienie użytkownika
```
Nowy SW zainstalowany
     ↓
showUpdateNotification() wyświetla powiadomienie
     ↓
"🎉 Nowa wersja aplikacji jest dostępna!"
     ↓
Użytkownik klika "Aktualizuj"
```

### Krok 3: Aktywacja nowego SW
```
Użytkownik kliknął "Aktualizuj"
     ↓
Wysłanie wiadomości: SKIP_WAITING
     ↓
Nowy SW przejmuje kontrolę
     ↓
controllerchange event
     ↓
Automatyczne przeładowanie strony
```

### Krok 4: Czyszczenie starego cache
```
Nowy SW aktywny
     ↓
activate event w sw.js
     ↓
Usunięcie wszystkich starych cache (dziennik-v1, dziennik-v1.9, etc.)
     ↓
Tylko dziennik-v2.0 pozostaje
```

---

## 📊 Scenariusze aktualizacji

### Scenariusz A: Normalna aktualizacja (zainstalowana PWA)
```
1. Deweloper publikuje nową wersję (zmienia sw.js i APP_VERSION)
2. Użytkownik otwiera aplikację
3. Service Worker wykrywa zmianę w sw.js (po max. 60 sek)
4. Powiadomienie: "Nowa wersja dostępna"
5. Użytkownik klika "Aktualizuj"
6. Strona się przeładowuje z nową wersją
7. Powiadomienie: "Zaktualizowano do wersji 2.0!"
✅ Gotowe - dane użytkownika nietknięte
```

### Scenariusz B: Aktualizacja w przeglądarce (nie PWA)
```
1. Deweloper publikuje nową wersję
2. Użytkownik otwiera aplikację w przeglądarce
3. localStorage wykrywa zmianę wersji
4. Stary cache jest czyszczony
5. Powiadomienie: "Zaktualizowano do wersji 2.0!"
6. Użytkownik kontynuuje pracę
✅ Gotowe - dane użytkownika nietknięte
```

### Scenariusz C: Ręczne sprawdzenie
```
1. Użytkownik otwiera menu → ℹ️ O aplikacji
2. Klika "🔄 Sprawdź aktualizacje"
3. Przycisk zmienia się: "⏳ Sprawdzam..."
4. Service Worker wykonuje reg.update()
5. Jeśli jest aktualizacja: powiadomienie jak w Scenariuszu A
6. Jeśli nie ma: przycisk pokazuje "✅ Aktualna wersja"
✅ Gotowe
```

---

## 🎨 Interfejs użytkownika

### Powiadomienie o aktualizacji SW:
```
┌─────────────────────────────────────────────┐
│ 🎉 Nowa wersja aplikacji jest dostępna!    │
│                                  [Aktualizuj]│
└─────────────────────────────────────────────┘
```

### Powiadomienie o zakończonej aktualizacji:
```
┌──────────────────────────────────────────────┐
│ 🎉  Zaktualizowano do wersji 2.0!           │
│     Kliknij "Aktualizacje" w menu,          │
│     aby zobaczyć co nowego            [OK]  │
└──────────────────────────────────────────────┘
```

### Przycisk w modalu:
```
Wersja 2.0 · © 2025–2026         [🔄 Sprawdź aktualizacje]
```

---

## 🔐 Bezpieczeństwo danych

### ✅ Dane użytkownika są bezpieczne:
- ❌ **NIE** jest czyszczony `localStorage` (dziennik_v5, dziennik_backup)
- ❌ **NIE** są usuwane klasy, pule, historia losowań
- ✅ Czyszczony jest tylko **cache** Service Workera (pliki HTML/JS/CSS)
- ✅ Użytkownik nie traci żadnych danych po aktualizacji

### Czyszczone podczas aktualizacji:
```javascript
caches.keys().then(keys => {
  keys.filter(k => k !== CACHE).map(k => caches.delete(k))
  // Usuwa: dziennik-v1, dziennik-v1.9, etc.
  // Zostawia: dziennik-v2.0
});
```

### NIE czyszczone:
```javascript
localStorage.getItem('dziennik_v5')      // ✅ Zostaje
localStorage.getItem('dziennik_backup')  // ✅ Zostaje
localStorage.getItem('darkMode')         // ✅ Zostaje
localStorage.getItem('appVersion')       // ✅ Aktualizowane (nie usuwane)
```

---

## 🧪 Testowanie mechanizmu

### Test 1: Symulacja aktualizacji
1. Zainstaluj PWA w wersji 2.0
2. Zmień `APP_VERSION` na `2.1` w kodzie
3. Zmień `CACHE` w sw.js na `dziennik-v2.1`
4. Wgraj nową wersję na serwer
5. Otwórz zainstalowaną PWA
6. Po max. 60 sek powinieneś zobaczyć powiadomienie
7. Kliknij "Aktualizuj"
8. Strona przeładuje się z wersją 2.1
9. Sprawdź: Dane (klasy, losowania) powinny pozostać nietknięte

### Test 2: Sprawdzenie ręczne
1. Otwórz aplikację
2. Menu → ℹ️ O aplikacji
3. Kliknij "🔄 Sprawdź aktualizacje"
4. Przycisk powinien pokazać "✅ Aktualna wersja" (jeśli brak aktualizacji)

### Test 3: Czyszczenie starego cache
1. Otwórz DevTools → Application → Cache Storage
2. Przed aktualizacją: Zobacz `dziennik-v2.0`
3. Zaktualizuj do v2.1
4. Po aktualizacji: Zobacz tylko `dziennik-v2.1`
5. Stary cache został usunięty ✅

---

## 📝 Checklist dla dewelopera

Przy każdym wydaniu nowej wersji:

- [ ] Zaktualizuj `APP_VERSION` (np. '2.0' → '2.1')
- [ ] Zaktualizuj `CACHE` w sw.js (np. 'dziennik-v2.0' → 'dziennik-v2.1')
- [ ] Dodaj wpis do tablicy `UPDATES` w index.html
- [ ] Zaktualizuj README.md (sekcja Historia wersji)
- [ ] Zaktualizuj CHANGELOG (nowy plik lub wpis)
- [ ] Wgraj wszystkie pliki na serwer
- [ ] Poczekaj 60 sekund
- [ ] Sprawdź czy powiadomienie się pojawia
- [ ] Przetestuj aktualizację
- [ ] Sprawdź czy stary cache został usunięty

---

## 🎓 Dobre praktyki

### DO ✅
- Zawsze zmieniaj wersję cache w sw.js przy każdej zmianie kodu
- Zawsze aktualizuj APP_VERSION w index.html
- Testuj aktualizacje na urządzeniu testowym przed produkcją
- Dodawaj changelog dla każdej wersji
- Utrzymuj konsystentne numerowanie wersji

### NIE ROBIĆ ❌
- Nie używaj tej samej wersji cache dla różnych wersji aplikacji
- Nie modyfikuj plików bez zmiany wersji
- Nie czyść localStorage podczas aktualizacji (stracisz dane użytkowników!)
- Nie wymuszaj aktualizacji bez zgody użytkownika
- Nie blokuj aplikacji gdy aktualizacja jest dostępna

---

## 🚀 Rezultaty

### Przed mechanizmem auto-update:
- ❌ Użytkownicy widzieli starą wersję przez tygodnie
- ❌ Musieli ręcznie czyścić cache
- ❌ Często zgłaszano "aplikacja się nie aktualizuje"
- ❌ Wsparcie techniczne zajmowało dużo czasu

### Po mechanizmie auto-update:
- ✅ Aktualizacje dostarczane automatycznie w ciągu 1-60 sekund
- ✅ Przyjazne powiadomienie dla użytkownika
- ✅ Jeden klik = aktualizacja gotowa
- ✅ Dane użytkownika bezpieczne
- ✅ Mniej zgłoszeń do wsparcia technicznego

---

## 📞 Troubleshooting

### Problem: Powiadomienie nie pojawia się
**Rozwiązanie:** Sprawdź czy:
1. Service Worker jest zarejestrowany (DevTools → Application → Service Workers)
2. Wersja cache w sw.js została zmieniona
3. Plik sw.js został zaktualizowany na serwerze
4. Minęło co najmniej 60 sekund od otwarcia aplikacji

### Problem: Aktualizacja się nie instaluje
**Rozwiązanie:**
1. Sprawdź console logs w DevTools
2. Odinstaluj PWA całkowicie
3. Wyczyść cache przeglądarki
4. Zainstaluj PWA ponownie

### Problem: Dane użytkownika zniknęły
**Przyczyna:** localStorage został wyczyszczony (nie powinno się to wydarzyć!)
**Rozwiązanie:**
1. Sprawdź czy jest backup: `localStorage.getItem('dziennik_backup')`
2. Przywróć z backupu
3. Zgłoś bug - mechanizm nie powinien czyścić localStorage

---

**Wersja dokumentacji:** 2.0  
**Data:** 2026-05-07  
**Autor:** Krzysztof Jureczek
