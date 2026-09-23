# Bieżący sprint v2

## Sprint
Sprint 02 — ukończony 2026-09-23

## Daty
Początek: 2026-09-22
Koniec: 2026-10-05

## Powiązany etap roadmapy
ETAP 0 — Środowisko i fundamenty

## Bieżąca wersja projektu
V0 / konfiguracja — repozytorium dokumentacyjne, bez aplikacji i testów

## Cel sprintu
Praktycznie zrozumieć podstawy HTTP/REST, wykonać i zinterpretować żądania do testowego API oraz zebrać dowody pozwalające ocenić ukończenie ETAPU 0.

## Nauka — maks. 3 tematy
- [x] Żądanie i odpowiedź HTTP: metoda, URL, nagłówki i body.
- [x] Podstawowe metody i kody stanu: GET, POST, 2xx, 4xx i 5xx.
- [x] REST i JSON na poziomie praktycznym.

## Budowanie — maks. 3 rezultaty
1. [x] Wykonano żądanie GET do testowego API i rozpoznano elementy żądania oraz odpowiedzi.
2. [x] Wykonano żądanie z JSON, odczytano status, nagłówki i body oraz wyjaśniono wynik.
3. [x] Dowody zapisano w `07_LEARNING_LOG.md` i przeprowadzono przegląd końcowy ETAPU 0.

## Sprawdzenie wiedzy
- [x] Potrafię własnymi słowami wyjaśnić różnicę między żądaniem a odpowiedzią.
- [x] Potrafię przewidzieć typowe zastosowanie metod GET i POST.
- [x] Potrafię wyjaśnić znaczenie otrzymanych kodów stanu i ich grup.
- [x] Potrafię odróżnić protokół HTTP od formatu danych JSON.
- [x] Potrafię samodzielnie wykonać proste żądanie bez komendy podanej przez AI.

## Kryteria ukończenia sprintu
- [x] Testowe żądania kończą się czytelną odpowiedzią.
- [x] Potrafię wskazać metodę, URL, status, nagłówki i body.
- [x] Potrafię własnymi słowami wyjaśnić wynik żądania.
- [x] W `07_LEARNING_LOG.md` istnieje praktyczny dowód wykonania ćwiczenia.
- [x] Przeprowadzono przegląd kryteriów ukończenia ETAPU 0.

## Carry-over ze Sprintu 01
- Docker/PostgreSQL: dalsza samodzielność utrwalana przy okazji naturalnej pracy z kontenerami, bez osobnego mechanicznego powtarzania laboratorium.

## Nie robimy w tym sprincie
- Nie rozpoczynamy implementacji ASP.NET Core ani V1.
- Nie projektujemy modelu domenowego, bazy aplikacji, autoryzacji ani architektury usług.
- Nie wprowadzamy Docker Compose.
- Nie wprowadzamy chmury, AI, RAG, Service Bus ani innych tematów z późniejszych etapów.

## Lista odłożonych tematów
- Implementacja API V1 — dopiero po ukończeniu ETAPU 0.

## Blokady
- Brak.

## Czas utknięcia
Jeżeli jeden problem przekracza 2–3 h:
- [ ] zapisałem hipotezę i wykonane kroki diagnostyczne
- [ ] użyłem Tutora do diagnostyki
- [ ] zdecydowałem: pogłębić teraz / wrócić później

## Wykorzystanie AI
### Inżynier
- Wykonuje żądania samodzielnie; prosi o pomoc po zapisaniu własnej interpretacji wyniku lub hipotezy błędu.

### Tutor
- Pomaga rozróżnić elementy żądania i odpowiedzi oraz wyjaśnia wynik bez wykonywania ćwiczenia za dewelopera.

### Recenzent
- Po zakończeniu sprintu sprawdza wyniki żądań, wyjaśnienie elementów HTTP i samodzielność wykonania.

# Retrospektywa
## Dowiezione
- Wykonałem proste żadania GET i POST, dane były przekazywane też w JSON

## Czego się nauczyłem
- Jak wykonać żadanie
- Kody statusów
- Różnica między GET a POST
- Do czego słuzy ContentType
- Sposób przekazania danych

## Co nadal umiem tylko z pomocą
- W tym sprincie nie stwierdzono blokującej luki w HTTP/REST. Docker i PostgreSQL pozostają na poziomie 2/5 i wymagają dalszej samodzielnej praktyki.

## Rozszerzanie zakresu
- Brak

## Co przechodzi dalej
- Samodzielna diagnostyka Docker/PostgreSQL w naturalnej pracy z projektem.
- Git: rozwiązywanie konfliktów, rebase i stash oraz podstawy Linux/bash — luki nieblokujące do dalszej praktyki.
