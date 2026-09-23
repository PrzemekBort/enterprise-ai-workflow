# Przeglądy v2

# Zamknięcie Sprintu 02 i przegląd ETAPU 0

### Data: 2026-09-23

## Dowody
- GET `/get?temat=http` zwrócił `200`, a parametr `temat` był widoczny w `args`.
- POST `/post` zwrócił `200`; bez nagłówka `Content-Type: application/json` dane były odczytane jako formularz, a z nim jako JSON.
- Deweloper wskazał metodę, URL, nagłówki, body oraz wyjaśnił grupy kodów stanu, `201`, `404` i różnicę między HTTP a JSON.
- Pierwsze żądania wykonano z pomocą AI, kolejne samodzielnie; dowód zapisano w `07_LEARNING_LOG.md` i przedstawiono w wynikach PowerShell.

## Ocena Sprintu 02
- Wszystkie kryteria Sprintu 02 są spełnione. Sprint zamknięto przed planowaną datą 2026-10-05.
- HTTP/REST: 3/5 — samodzielne podstawowe użycie; brak dowodu na poziom 4 (diagnostyka typowych problemów).

## Przegląd etapowy — ETAP 0
- [x] Środowisko działa: Git, .NET, Python i Docker są dostępne, a PostgreSQL działa w kontenerze.
- [x] Samodzielnie wykonano przepływ Git: gałąź → commit → scalenie.
- [x] Kontener i PostgreSQL odpowiadały na zapytanie przed i po restarcie.
- [x] Wykonano i wyjaśniono żądania HTTP GET i POST.
- [x] Kryteria blokujące ETAPU 0 są spełnione.

## Luki nieblokujące
- Docker/PostgreSQL: poziom 2/5; większą samodzielność utrwalać w naturalnej pracy z projektem.
- Git: konflikty, rebase i stash; podstawy Linux/bash — dalsza praktyka bez osobnego warunku przejścia.

## Decyzja
- ETAP 0 ukończony. Następny krok: zaplanowanie Sprintu 03 w ETAPIE 1 dla pierwszego, ograniczonego zakresu V1.

---

# Zamknięcie Sprintu 01

### Data: 2026-09-22

## Realizacja
- Sprint 01 został ukończony.
- Środowisko lokalne działa: Git, .NET, Python i Docker są dostępne.
- Samodzielnie wykonano przepływ Git: gałąź → commit → scalenie.
- PostgreSQL uruchomiony w Dockerze odpowiedział na zapytanie przed i po restarcie kontenera.

## Kompetencje i dowody
- Git/GitHub: 3/5 — samodzielne użycie.
- Docker: 2/5 — rozumienie i użycie z pomocą.
- PostgreSQL: 2/5 — rozumienie i użycie z pomocą.

## Zakres i carry-over
- Nie rozszerzano zakresu poza ETAP 0.
- Dalsza samodzielność Docker/PostgreSQL będzie utrwalana w naturalnej pracy z kontenerami, bez osobnego mechanicznego powtarzania laboratorium.

## Decyzja
- Pozostaję w ETAPIE 0.
- Rozpoczynam Sprint 02 poświęcony HTTP/REST i przygotowaniu do przeglądu końcowego etapu.

---

# Przegląd tygodniowy

### Tydzień: YYYY-WXX

## Realizacja
**Planowane cele:**
1.
2.
3.

**Wykonane:**
-

**Niewykonane:**
-

## Nauka / Budowanie / Wiedza
**Czego się nauczyłem:**
-

**Co zbudowałem:**
-

**Co potrafię teraz zrobić bez AI:**
-

## Ryzyka
- Utknąłem > 2–3 h:
- Rozszerzanie zakresu:
- Za dużo delegacji do AI:
- Plan był zbyt szeroki:

## Następny tydzień — maks. 3 cele
1.
2.
3.

---

# Przegląd miesięczny

### Miesiąc: YYYY-MM

## Roadmapa
- Aktualny etap:
- Nauka:
- Budowanie:
- Sprawdzenie wiedzy:
- Kryteria ukończenia:

## Kompetencje
- Największy wzrost:
- Tematy powierzchowne:
- Tematy blokujące zbyt długo:
- Co potrafię debugować:

## Regularność
- planowane godziny:
- rzeczywiste godziny:
- aktywne tygodnie:
- tygodnie 0h:

## Wykorzystanie AI
- gdzie AI pomogło:
- gdzie zrobiło za dużo:
- co następnym razem zrobię sam:

## Zakres
- nowe technologie:
- potrzebne / niepotrzebne:
- co trafia do `LATER.md`:

## Decyzja
- [ ] kontynuuję
- [ ] ograniczam zakres
- [ ] wracam do jednej luki
- [ ] świadomie koryguję roadmapę

---

# Przegląd etapowy — po etapie

### Etap:
### Data:

## Nauka
- [ ] kluczowe pojęcia są zrozumiane

## Budowanie
- [ ] wymagane elementy istnieją w projekcie

## Sprawdzenie wiedzy
- [ ] potrafię wyjaśnić kluczowe pojęcia
- [ ] potrafię wykonać podstawowe zadania bez prowadzenia AI
- [ ] potrafię debugować typowe problemy
- [ ] potrafię obronić główne decyzje techniczne

## Kryteria ukończenia
- [ ] wszystkie kryteria blokujące są spełnione

## Luki blokujące
-

## Luki nieblokujące / do ponownego rozważenia
-

## Czy siedzę w etapie za długo?
-

## Czy próbuję osiągnąć perfekcję?
-

## Decyzja
- [ ] przechodzę dalej
- [ ] +1 tydzień
- [ ] +2 tygodnie
- [ ] większa korekta roadmapy

## Uzasadnienie
-
