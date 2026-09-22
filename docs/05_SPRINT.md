# Bieżący sprint v2

## Sprint
Sprint 01

## Daty
Początek: 2026-08-29
Koniec: 2026-09-11

## Powiązany etap roadmapy
ETAP 0 — Środowisko i fundamenty

## Bieżąca wersja projektu
V0 / konfiguracja — repozytorium dokumentacyjne, bez aplikacji i testów

## Cel sprintu
Uzyskać powtarzalny, samodzielnie sprawdzony fundament pracy: zweryfikowane narzędzia lokalne, pełny przepływ Git oraz działające kontenery Docker z lokalnym PostgreSQL.

## Nauka — maks. 3 tematy
- [x] Git: różnica między commitem, gałęzią i scaleniem oraz ich ślad w historii.
- [x] Terminal: rozpoznawanie braku instalacji i problemu z `PATH`.
- [x] Docker i PostgreSQL: kontener, port, proces bazy oraz podstawowe połączenie.

## Budowanie — maks. 3 rezultaty
1. [x] Udokumentowana w `07_LEARNING_LOG.md` weryfikacja środowiska: Git, .NET, Python i Docker odpowiadają na polecenia wersji; sposób dostępu do PostgreSQL jest znany.
2. [x] W repozytorium wykonano na małej zmianie przepływ gałąź → commit → scalenie, a deweloper potrafi wskazać rezultat w historii Git.
3. [x] Uruchomiono prosty kontener oraz lokalny PostgreSQL; połączenie z bazą i proste zapytanie kończą się powodzeniem.

## Sprawdzenie wiedzy
- [x] Potrafię własnymi słowami wyjaśnić różnicę między commitem, gałęzią i scaleniem oraz przewidzieć stan historii po scaleniu.
- [x] Potrafię bez instrukcji krok po kroku utworzyć gałąź, zapisać małą zmianę w commicie i scalić ją z `main`.
- [x] Potrafię zdiagnozować, czy niedziałające polecenie lub połączenie z kontenerem wynika z instalacji, `PATH`, stanu kontenera czy mapowania portu.

## Kryteria ukończenia sprintu
- [x] Wszystkie narzędzia potrzebne do zadań sprintu są dostępne i ich stan jest zapisany w dzienniku nauki.
- [x] Historia Git zawiera sprawdzalny rezultat samodzielnego przepływu gałąź → commit → scalenie.
- [x] Docker uruchamia kontenery, a PostgreSQL odpowiada na proste zapytanie po ponownym uruchomieniu środowiska.

## Nie robimy w tym sprincie
- Nie rozpoczynamy implementacji ASP.NET Core ani V1.
- Nie projektujemy modelu domenowego, bazy aplikacji, autoryzacji ani architektury usług.
- Nie wprowadzamy chmury, AI, RAG, Service Bus ani innych tematów z późniejszych etapów.
- Ćwiczenie HTTP/REST pozostaje wymaganiem ETAPU 0, ale nie jest rezultatem tego sprintu.

## Lista odłożonych tematów
- Proste żądanie HTTP do testowego API — następny ograniczony krok w ETAPIE 0 po ustabilizowaniu środowiska.

## Blokady
- Brak

## Czas utknięcia
- Brak

## Wykorzystanie AI
### Inżynier
- Wykonuje konfigurację i zadania samodzielnie; prosi o pomoc po zapisaniu własnej hipotezy i wyniku diagnostyki.

### Tutor
- Zadaje pytania naprowadzające, pomaga odróżnić brak instalacji od problemu z `PATH` i nie wykonuje ćwiczenia za dewelopera.

### Recenzent
- Po zakończeniu sprintu sprawdza dowody: historię Git, zapis poleceń w dzienniku oraz powtarzalne uruchomienie PostgreSQL.

# Retrospektywa
## Dowiezione
Instalacja niezbędnych narzedzi

## Czego się nauczyłem
Obsługa gita, branchy i merge
Podstawowa obsługa dockera

## Co nadal umiem tylko z pomocą
Obsługa dockera

## Rozszerzanie zakresu
Brak rozszerzania zakresu

## Co przechodzi dalej
Diagnostyka i dlasza praca z dockerem
Ćwiczenie HTTP/REST, jeżeli nie zostanie podjęte po osiągnięciu celu sprintu.