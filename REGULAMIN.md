# 📄 Regulamin aplikacji Dziennik Losowań

**Wersja 1.0 · obowiązuje od 17 kwietnia 2026 r.**

---

## §1. Postanowienia ogólne

Niniejszy Regulamin określa zasady korzystania z aplikacji internetowej **Dziennik Losowań** (dalej: „Aplikacja"), udostępnianej pod adresem **https://krzjur-oss.github.io/dziennik-losowan/**.

Właścicielem i twórcą Aplikacji jest **Krzysztof Jureczek** (dalej: „Autor"). Korzystanie z Aplikacji jest równoznaczne z akceptacją niniejszego Regulaminu.

---

## §2. Przeznaczenie Aplikacji

Aplikacja przeznaczona jest wyłącznie do **niekomercyjnego użytku w placówkach oświatowych** (szkoły, przedszkola, placówki kształcenia). Umożliwia losowe wybieranie uczniów podczas zajęć lekcyjnych — zarządzanie klasami, pulami numerów, rejestrowaniem nieobecności oraz prowadzeniem historii losowań.

---

## §3. Warunki korzystania

- Aplikacja jest bezpłatna i dostępna dla każdego użytkownika posiadającego dostęp do przeglądarki internetowej.
- Użytkownik zobowiązuje się korzystać z Aplikacji zgodnie z jej przeznaczeniem oraz obowiązującym prawem.
- Zabronione jest używanie Aplikacji w celach komercyjnych bez pisemnej zgody Autora.
- Zabronione jest podejmowanie działań mogących zakłócić działanie Aplikacji lub narazić innych użytkowników na szkodę.

---

## §4. Prawa autorskie i licencja

Wszelkie prawa do Aplikacji — w tym kod źródłowy, interfejs graficzny, projekt wizualny oraz dokumentacja — należą wyłącznie do Autora i są chronione przepisami prawa autorskiego.

| | |
|---|---|
| ❌ **Zabronione** | Kopiowanie, modyfikowanie, dekompilowanie, rozpowszechnianie lub sprzedaż Aplikacji bądź jej części bez pisemnej zgody Autora |
| ✅ **Dozwolone** | Korzystanie z Aplikacji zgodnie z jej przeznaczeniem oraz udostępnianie linku do Aplikacji innym osobom |

W sprawach licencjonowania komercyjnego prosimy o kontakt z Autorem poprzez repozytorium GitHub.

---

## §5. Dane i prywatność

Aplikacja **nie zbiera, nie przesyła ani nie przechowuje** żadnych danych użytkownika na zewnętrznych serwerach. Wszelkie dane (lista klas, pule numerów, historia losowań, nieobecności) przechowywane są wyłącznie lokalnie w pamięci przeglądarki użytkownika (`localStorage`) na jego urządzeniu.

- Dane nie opuszczają urządzenia użytkownika.
- Aplikacja nie używa plików cookie, narzędzi analitycznych ani reklam.
- Użytkownik może w każdej chwili usunąć swoje dane, czyszcząc dane przeglądarki lub korzystając z funkcji eksportu/importu JSON.

### Klucze localStorage używane przez Aplikację

| Klucz | Zawartość |
|-------|-----------|
| `dziennik_v5` | Pełny stan aplikacji (klasy, pule, historia losowań, nieobecności) |
| `dziennik_backup` | Automatyczna kopia zapasowa stanu aplikacji |

---

## §6. Odpowiedzialność

Aplikacja udostępniana jest w stanie „takim, jakim jest" (*as is*), bez jakichkolwiek gwarancji — w szczególności gwarancji przydatności do określonego celu czy nieprzerwanego działania.

- Autor nie ponosi odpowiedzialności za utratę danych wynikającą z wyczyszczenia danych przeglądarki, awarii urządzenia lub innych przyczyn niezależnych od Autora.
- Autor nie ponosi odpowiedzialności za szkody wynikające z nieprawidłowego korzystania z Aplikacji.
- Zaleca się regularne tworzenie kopii zapasowych danych za pomocą funkcji **⇅ Eksportuj JSON**.

---

## §7. Zmiany Regulaminu

Autor zastrzega sobie prawo do zmiany Regulaminu. O istotnych zmianach użytkownicy będą informowani poprzez komunikat wyświetlany w Aplikacji. Dalsze korzystanie z Aplikacji po opublikowaniu zmian oznacza ich akceptację.

---

## §8. Postanowienia końcowe

W sprawach nieuregulowanych niniejszym Regulaminem zastosowanie mają przepisy prawa polskiego, w szczególności Kodeksu cywilnego oraz ustawy o prawie autorskim i prawach pokrewnych.

Wszelkie pytania dotyczące Aplikacji lub niniejszego Regulaminu można kierować do Autora za pośrednictwem repozytorium GitHub projektu: **https://github.com/krzjur-oss/dziennik-losowan**

---

*© 2025–2026 Krzysztof Jureczek · Wszelkie prawa zastrzeżone*
