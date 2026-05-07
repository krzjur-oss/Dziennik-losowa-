# 🎉 Dziennik Losowania v2.0 - Zgłaszanie się do odpowiedzi

## 🆕 Nowe funkcje

### 1. **Oznaczanie uczniów którzy się zgłosili**

Dodano możliwość oznaczania uczniów którzy sami zgłosili się do odpowiedzi (bez losowania).

#### Jak używać:
- **Podwójne kliknięcie** na numer ucznia = oznacz jako zgłoszonego
- **Ponowne podwójne kliknięcie** = usuń z listy zgłoszonych

#### Wizualne oznaczenie:
- 🔵 **Niebieskie tło** z emoji ✋
- Odmienny kolor od nieobecnych (czerwony ⊘)

#### Efekt:
- Zgłoszeni uczniowie **NIE biorą udziału w losowaniu**
- Są traktowani jak tymczasowo wykluczeni (podobnie jak nieobecni)
- Automatycznie usuwani z kolejki już wylosowanych

---

### 2. **Statystyki zgłoszonych**

W sekcji "Pula klasy" pojawia się licznik:
```
Zgłosili się: 3
```

Widoczny tylko gdy ktoś jest oznaczony jako zgłoszony.

---

### 3. **Szybkie czyszczenie listy zgłoszonych**

W menu **⚙️ Akcje klasy** pojawia się nowy przycisk:
```
🙋 Wyczyść zgłoszonych (3)
```

- Pojawia się tylko gdy ktoś jest zgłoszony
- Liczba w nawiasie pokazuje ile osób
- Jeden klik = wszyscy zgłoszeni z powrotem w puli

---

### 4. **Integracja z istniejącymi funkcjami**

Zgłoszeni są automatycznie usuwani przy:
- ☐ **Odznacz wszystkie**
- ① **Nieparzyste**
- ② **Parzyste**

---

### 5. **Ochrona przed konfliktem**

**Nie można** oznaczyć jako zgłoszonego ucznia który jest **nieobecny** (czerwony ⊘).

Priorytety:
1. Nieobecny (czerwony) - nadrzędny
2. Zgłoszony (niebieski) - tylko jeśli nie jest nieobecny
3. Wylosowany (złoty)
4. Aktywny (zielony)
5. Wykluczony (szary)

---

## 🎨 Legenda kolorów

| Kolor | Znaczenie | Emoji | Status |
|-------|-----------|-------|--------|
| 🟢 Zielony | Aktywny w puli | - | Może być wylosowany |
| 🟡 Złoty | Już wylosowany dziś | - | Nie będzie losowany ponownie |
| 🔵 Niebieski | Zgłosił się sam | ✋ | Nie bierze udziału w losowaniu |
| 🔴 Czerwony | Nieobecny | ⊘ | Nie bierze udziału w losowaniu |
| ⚫ Szary | Wykluczony na stałe | - | Nie bierze udziału w losowaniu |

---

## 📱 Obsługa na różnych urządzeniach

### Desktop (komputer):
- **Pojedyncze kliknięcie** = włącz/wyłącz z puli
- **Podwójne kliknięcie** = oznacz jako zgłoszonego
- **Prawy przycisk myszy** = oznacz jako nieobecnego

### Mobile (telefon/tablet):
- **Pojedyncze dotknięcie** = włącz/wyłącz z puli
- **Podwójne dotknięcie** = oznacz jako zgłoszonego
- **Długie przytrzymanie (600ms)** = oznacz jako nieobecnego

---

## 💡 Przykładowe scenariusze użycia

### Scenariusz 1: Rozpoczęcie zajęć
1. Oznacz nieobecnych (długie przytrzymanie / prawy przycisk)
2. Poproś kto chce się zgłosić do odpowiedzi
3. Oznacz zgłoszonych (podwójne kliknięcie)
4. **Losuj** pozostałych uczniów

### Scenariusz 2: Środek lekcji
1. Kolejni uczniowie zgłaszają się sami
2. Podwójnie klikasz ich numery
3. Losowanie obejmuje tylko tych którzy się NIE zgłosili

### Scenariusz 3: Koniec lekcji
1. Kliknij **🙋 Wyczyść zgłoszonych**
2. Wszyscy wracają do puli na następną lekcję

---

## 🔄 Kompatybilność z poprzednią wersją

- ✅ Plik eksportu z v1.x można importować do v2.0
- ✅ Istniejące dane pozostają nienaruszone
- ✅ Nowe pole `volunteered` jest automatycznie dodawane

---

## 🐛 Uwagi techniczne

### Struktura danych klasy:
```javascript
{
  id: "class_123",
  name: "2a",
  poolSize: 30,
  drawCount: 2,
  pool: [{n: 1, included: true}, ...],
  drawnQueue: [5, 12],
  absent: [3, 7],           // Nieobecni
  volunteered: [15, 22],    // Zgłoszeni ⬅️ NOWE
  history: [...]
}
```

### Logika wykluczania z losowania:
```javascript
// Aktywni = Włączeni - Nieobecni - Zgłoszeni
const active = cls.pool
  .filter(p => p.included)
  .filter(p => !absent.includes(p.n))
  .filter(p => !volunteered.includes(p.n))
  .map(p => p.n);
```

---

## 📋 Pełna lista zmian v2.0

1. ✅ Dodano `toggleVolunteered(cid, n)` - przełączanie stanu zgłoszony/nie
2. ✅ Dodano `clearVolunteered(cid)` - czyszczenie listy zgłoszonych
3. ✅ Zaktualizowano `buildClassView()` - renderowanie z uwzględnieniem volunteered
4. ✅ Zaktualizowano `selectAll/deselectAll/selectOdd/selectEven` - czyszczenie volunteered
5. ✅ Dodano `ondblclick` event na przyciskach num-btn
6. ✅ Dodano style CSS `.num-btn.volunteered`
7. ✅ Dodano zmienną `--accent2` (niebieski #1a4a8b)
8. ✅ Zaktualizowano legendę w opisie puli
9. ✅ Dodano licznik zgłoszonych w pool-stats
10. ✅ Dodano przycisk "Wyczyść zgłoszonych" w menu akcji
11. ✅ Zaktualizowano `loadState()` i import - inicjalizacja `volunteered: []`
12. ✅ Dodano wpis do tablicy UPDATES

---

## 🚀 Instalacja

1. Skopiuj wszystkie pliki:
   - `index.html`
   - `manifest.json`
   - `sw.js`
   - `icon-192.png`
   - `icon-512.png`

2. Otwórz w przeglądarce

3. (Opcjonalnie) Zainstaluj jako PWA:
   - Chrome/Edge: Menu → Zainstaluj aplikację
   - Safari (iOS): Udostępnij → Dodaj do ekranu głównego

---

## 📞 Wsparcie

Aplikacja autorstwa: **Krzysztof Jureczek**  
Wersja: **2.0**  
Data wydania: **2026-05-07**

---

**Dobrej zabawy z nową funkcją! 🎲**
