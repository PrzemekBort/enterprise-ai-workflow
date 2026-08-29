# Enterprise AI Workflow — Wymagania projektu

## 1. Cel
`Enterprise AI Workflow` to ogólna wewnętrzna aplikacja korporacyjna do obsługi wniosków biznesowych, dokumentów, zatwierdzeń, historii przepływu pracy, a w późniejszych wersjach także przetwarzania i działań wspomaganych przez AI.

Ten dokument określa **co system powinien robić**, a nie jak ma zostać zaimplementowany. Decyzje architektoniczne i implementacyjne, które nie zostały tu jednoznacznie ograniczone, pozostają w gestii dewelopera.

## 2. Główna koncepcja biznesowa
Użytkownik tworzy wewnętrzny wniosek biznesowy. Wniosek może zawierać dane i dokumenty. Może przechodzić przez kontrolowany przepływ pracy, podlegać przeglądowi, zatwierdzeniu lub odrzuceniu oraz zachowywać historię ważnych działań.

Z czasem system zyskuje:
- przetwarzanie dokumentów,
- wdrożenie w chmurze,
- ekstrakcję danych z dokumentów opartą na LLM,
- wyszukiwanie wiedzy przedsiębiorstwa / RAG,
- wywoływanie narzędzi przez AI,
- tożsamość korporacyjną i autoryzację,
- obserwowalność i niezawodność produkcyjną.

## 3. Główne pojęcia biznesowe
System powinien docelowo reprezentować:
- **Użytkownika** — osobę korzystającą z systemu,
- **Wniosek** — wniosek biznesowy,
- **Dokument** — plik powiązany z wnioskiem,
- **Zatwierdzenie** — decyzję powiązaną z wnioskiem,
- **Zadanie** — pracę wynikającą z procesu,
- **Zdarzenie audytowe** — zapis ważnego działania lub zmiany stanu.

Nie narzuca to oddzielnych encji, agregatów, modułów ani usług.

## 4. Cykl życia wniosku

Początkowy cykl życia w V1 jest celowo prosty:

```text
Wersja robocza
  ↓
Złożony
  ├──→ Zatwierdzony
  └──→ Odrzucony
```

Stany `W trakcie przeglądu`, `Ukończony` i inne mogą zostać wprowadzone później tylko wtedy, gdy uzasadnia je konkretne wymaganie biznesowe.

System musi:
- odrzucać nieprawidłowe przejścia stanów,
- zachowywać ważną historię cyklu życia,
- jednoznacznie przedstawiać bieżący stan.

Otwarte decyzje obejmują reguły przejść, modelowanie zatwierdzeń i umiejscowienie logiki przepływu pracy.

---

# 5. V1 — Zarządzanie wnioskami

## Cel biznesowy
Pracownik może utworzyć i złożyć wniosek. Upoważniony recenzent może go zatwierdzić lub odrzucić. Ważne działania pozostają widoczne w historii.

W V1 tożsamość użytkownika i uprawnienia recenzenta mogą być symulowane lub reprezentowane przez uproszczony mechanizm na poziomie aplikacji. Tożsamość i autoryzacja klasy produkcyjnej zostają wprowadzone w V7.

## Wymagane możliwości
- utworzenie wniosku,
- pobranie jednego wniosku,
- wyświetlenie listy wniosków,
- modyfikowanie dozwolonych danych w odpowiednim stanie,
- złożenie wniosku,
- zatwierdzenie wniosku,
- odrzucenie wniosku,
- wyświetlenie historii wniosku.

## Minimalne informacje o wniosku
- unikalny identyfikator,
- autor,
- tytuł,
- opis,
- status,
- znacznik czasu utworzenia,
- znacznik czasu ostatniej modyfikacji.

## Reguły biznesowe
- zatwierdzenie jest dozwolone tylko z prawidłowych stanów,
- odrzucenie jest dozwolone tylko z prawidłowych stanów,
- nieprawidłowe przejścia są odrzucane,
- nieprawidłowe dane wejściowe nie mogą bez powiadomienia tworzyć niespójnych danych,
- ważne operacje zmieniające stan są rejestrowane.

## Oczekiwania dotyczące audytu
System powinien odpowiadać na pytanie: **kto wykonał jakie działanie, kiedy i na którym wniosku?**

Przykładowe zdarzenia:
- `RequestCreated`
- `RequestUpdated`
- `RequestSubmitted`
- `RequestApproved`
- `RequestRejected`

## Kryteria akceptacji
V1 jest ukończona, gdy:
- można utworzyć wniosek,
- może on przechodzić przez zamierzony cykl życia,
- nieprawidłowe przejścia są odrzucane,
- zatwierdzenie/odrzucenie działa tylko wtedy, gdy jest dozwolone,
- można pobrać bieżący stan,
- można pobrać istotną historię,
- nieprawidłowe dane wejściowe są bezpiecznie obsługiwane.

## Wyraźnie wykluczone wymagania
V1 nie wymaga:
- Entra ID,
- autoryzacji klasy produkcyjnej,
- AI,
- wdrożenia w chmurze,
- mikrousług,
- Service Bus,
- zaawansowanego przetwarzania dokumentów,
- złożonego interfejsu użytkownika.

---

# 6. V2 — Dokumenty i ich przetwarzanie

## Cel biznesowy
Wniosek może zawierać dokumenty. System może przetworzyć przesłany dokument oraz udostępnić stan i wynik przetwarzania.

## Wymagane informacje o dokumencie
- identyfikator,
- nazwa pliku,
- typ/typ zawartości,
- rozmiar,
- znacznik czasu przesłania,
- osoba przesyłająca,
- powiązanie z wnioskiem.

## Wymagane możliwości
- dołączenie dokumentu do wniosku,
- przyjęcie go do przetwarzania,
- wyodrębnienie podstawowego tekstu/zawartości bez AI,
- zapisanie wyniku lub odwołania do niego,
- wykrycie niepowodzenia przetwarzania,
- udostępnienie stanu przetwarzania,
- ponowienie nieudanego przetwarzania tam, gdzie jest to właściwe.

## Kryteria akceptacji
- dokumenty można dołączać,
- metadane są zachowywane,
- przetwarzanie może zakończyć się jawnym sukcesem lub niepowodzeniem,
- niepowodzenie nie pozostawia niezdefiniowanego stanu,
- ponowienie jest możliwe tam, gdzie jest dozwolone.

## Otwarte decyzje
- fizyczne miejsce przechowywania,
- własność metadanych,
- modelowanie encji/agregatów,
- kształt API,
- przetwarzanie synchroniczne lub asynchroniczne,
- komunikacja .NET ↔ Python,
- semantyka ponowień.

---

# 7. V3 — Wdrożenie w chmurze

## Cel biznesowy
Aplikacja działa jako system hostowany w chmurze Azure.

## Wymagane możliwości
- zaplecze aplikacji,
- baza danych,
- magazyn dokumentów,
- bezpieczna obsługa sekretów/konfiguracji,
- zautomatyzowane wdrożenie,
- monitorowanie.

## Kryteria akceptacji
- podstawowa aplikacja działa w Azure,
- wdrożenie jest powtarzalne,
- sekrety nie są przechowywane w kodzie źródłowym,
- stan i awarie są obserwowalne,
- baza danych i magazyn dokumentów działają z wdrożonej aplikacji.

Usługa chmurowa powinna być wprowadzana wyłącznie w celu spełnienia konkretnego wymagania.

---

# 8. V4 — Przetwarzanie dokumentów przez AI

## Cel biznesowy
System wykorzystuje LLM do wyodrębniania z dokumentów ustrukturyzowanych informacji biznesowych.

Przykład:

```text
Invoice.pdf
    ↓
    Przetwarzanie AI
    ↓
{
  "invoiceNumber": "...",
  "seller": "...",
  "amount": 1234.56,
  "currency": "PLN",
  "date": "..."
}
```

Schemat ma charakter przykładowy.

## Wymagane możliwości
- wysłanie wyodrębnionej zawartości do LLM,
- ustrukturyzowane dane wyjściowe,
- walidacja schematu,
- walidacja biznesowa,
- obsługa brakujących/nieprawidłowych wartości,
- ponowienie tam, gdzie jest uzasadnione,
- ręczny przegląd,
- akceptacja/odrzucenie ekstrakcji AI,
- audyt ważnych działań AI,
- pomiar podstawowego opóźnienia i kosztu.

## Główna zasada
**LLM nie jest źródłem prawdy.**

## Kryteria akceptacji
- co najmniej jeden typ dokumentu można przekształcić w ustrukturyzowane dane,
- nieprawidłowo sformatowane dane wyjściowe są obsługiwane,
- nieprawidłowe dane można odrzucić,
- człowiek może przejrzeć wyodrębnione dane,
- ważne działania podlegają audytowi,
- można obserwować opóźnienie i koszt.

## Otwarte decyzje
- typ dokumentu,
- schemat,
- prompty,
- model,
- reguły ponowień,
- sposób przedstawiania pewności,
- przebieg przeglądu,
- przechowywanie wyodrębnionych danych.

---

# 9. V5 — Asystent wiedzy przedsiębiorstwa

## Cel biznesowy
Użytkownik może zadawać pytania dotyczące dokumentów dostępnych w systemie i otrzymywać odpowiedzi poparte źródłami.

## Wymagane możliwości
- wprowadzanie dokumentów do przeszukiwalnego potoku,
- wyszukiwanie odpowiedniej zawartości,
- generowanie odpowiedzi z użyciem wyszukanej zawartości,
- wskazywanie materiału źródłowego.

## Główna zasada
Odpowiedź bez informacji o źródle nie stanowi kompletnej implementacji.

## Kryteria akceptacji
- użytkownik może zadać pytanie,
- odpowiednia zawartość zostaje wyszukana,
- odpowiedź zawiera odwołania do źródeł,
- jakość wyszukiwania można ocenić,
- niepowodzenia wyszukiwania można odróżnić od niepowodzeń generowania.

## Otwarte decyzje
- magazyn wektorowy,
- dzielenie na fragmenty,
- metadane,
- algorytm wyszukiwania,
- wyszukiwanie hybrydowe,
- ponowne szeregowanie wyników,
- zbiór danych i metryki do oceny.

---

# 10. V6 — Asystent AI i wywoływanie narzędzi

## Cel biznesowy
AI może wchodzić w interakcje z wybranymi funkcjami aplikacji, a nie tylko generować tekst.

Przykłady:
- `get_user_requests(...)`
- `submit_request(...)`

## Wymagane możliwości
- ograniczony, jawny zestaw narzędzi,
- walidacja parametrów,
- autoryzacja poza LLM,
- audyt działań,
- silniejsze mechanizmy kontroli dla działań zmieniających stan,
- bezpieczna obsługa awarii.

## Główne zasady
- LLM nie jest organem decydującym o autoryzacji,
- narzędzia nie ufają tożsamości/uprawnieniom wygenerowanym przez model,
- działania zmieniające stan wymagają silniejszych mechanizmów kontroli niż działania tylko do odczytu.

## Kryteria akceptacji
- działa co najmniej jedno narzędzie tylko do odczytu,
- działa co najmniej jedno kontrolowane narzędzie zmieniające stan,
- nieprawidłowe wywołania są odrzucane,
- nieautoryzowane wywołania są odrzucane,
- działania podlegają audytowi,
- obsługa awarii jest zdefiniowana.

## Otwarte decyzje
- kontrakty narzędzi,
- wymagania dotyczące potwierdzania,
- orkiestracja,
- granice usług,
- wykonywanie synchroniczne lub asynchroniczne,
- wykorzystanie komunikacji asynchronicznej.

---

# 11. V7 — Tożsamość i bezpieczeństwo przedsiębiorstwa

## Cel biznesowy
Użytkownicy i funkcje wspomagane przez AI przestrzegają rzeczywistych granic tożsamości i autoryzacji przedsiębiorstwa.

## Wymagane możliwości
- uwierzytelnianie Entra ID,
- role/zakresy lub ich odpowiednik,
- autoryzacja operacji biznesowych,
- uprawnienia do wniosków/dokumentów,
- RAG uwzględniający uprawnienia,
- zasada najmniejszych uprawnień,
- bezpieczna tożsamość w komunikacji między usługami,
- bezpieczna obsługa sekretów.

## Główna zasada bezpieczeństwa
**Jeżeli użytkownik nie może uzyskać dostępu do zasobu przez zwykłą aplikację/API, AI i RAG również nie mogą go ujawnić.**

## Kryteria akceptacji
- uwierzytelnieni użytkownicy mają możliwe do zidentyfikowania uprawnienia,
- nieautoryzowane operacje API są odrzucane,
- dokumenty bez uprawnień nie są ujawniane przez RAG,
- narzędzia AI wymuszają autoryzację niezależnie od modelu,
- tożsamości usług korzystają z najmniejszych uprawnień,
- istnieje podstawowy model zagrożeń.

---

# 12. V8 — Wzmocnienie produkcyjne

## Cel biznesowy
Aplikacja zachowuje się jak działający system, a nie tylko jak prototyp.

## Wymagane możliwości

### Obserwowalność
- logi,
- metryki,
- ślady,
- korelacja żądań,
- opóźnienie AI,
- wykorzystanie tokenów/koszt,
- znaczące informacje o stanie.

### Niezawodność
Tam, gdzie jest to uzasadnione:
- ponowienia,
- limity czasu,
- bezpieczniki,
- kolejki,
- buforowanie,
- zachowanie awaryjne.

### Jakość AI
- zbiór danych do oceny,
- oczekiwane zachowanie,
- ocena wyszukiwania,
- kontrole regresji,
- kontrole halucynacji/błędów.

### Infrastruktura i dokumentacja
- powtarzalna infrastruktura jako kod (IaC) dla kluczowych zasobów Azure,
- opis architektury,
- ważne decyzje,
- założenia operacyjne,
- README gotowy do portfolio.

## Kryteria akceptacji
- ważne żądania można prześledzić od początku do końca,
- typowe awarie można diagnozować na podstawie telemetrii,
- wdrożenie/infrastruktura są powtarzalne,
- mechanizmy niezawodności są stosowane celowo,
- zachowanie AI podlega powtarzalnej podstawowej ocenie,
- architektura i kompromisy są udokumentowane.

---

# 13. Globalne ograniczenia projektu

## Preferuj prostotę
Używaj najprostszej rozsądnej architektury, która spełnia wymagania **bieżącej** wersji.

## Technologia musi rozwiązywać problem
Nie wprowadzaj komunikacji asynchronicznej, mikrousług, buforowania, dodatkowych baz danych, platform orkiestracyjnych ani usług chmurowych tylko dlatego, że mogą przydać się później.

## Oczekiwana jest architektura rozwijana przyrostowo
Refaktoryzacja jest dozwolona i oczekiwana. Wczesne decyzje nie muszą przetrwać do V8.

## Jeden główny produkt
Głównym projektem pozostaje `Enterprise AI Workflow`. Małe laboratoria mogą służyć do nauki odizolowanych pojęć.

---

# 14. Poza zakresem, chyba że zostanie później wyraźnie dodane
- projekt wizualny klasy produkcyjnej,
- aplikacja mobilna,
- Kubernetes,
- niestandardowe trenowanie LLM,
- zaawansowany rozwój modeli uczenia maszynowego,
- pełny silnik BPMN/przepływu pracy,
- funkcjonalność w skali ERP,
- złożona wielodostępność,
- rozliczenia,
- dziesiątki typów przepływów pracy,
- mikrousługi dla każdego komponentu,
- wersje dla AWS/GCP.

Może istnieć prosty interfejs graficzny, ale inżynieria interfejsu użytkownika nie jest głównym wymaganiem.

---

# 15. Decyzje celowo pozostawione otwarte
Poniższe kwestie celowo nie zostały z góry określone:
- szczegóły modelu domenowego,
- schemat bazy danych,
- struktura rozwiązania/projektu,
- kontrolery lub minimalne API,
- model błędów,
- implementacja walidacji,
- implementacja audytu,
- implementacja przepływu pracy,
- granice modułów,
- komunikacja .NET ↔ Python,
- strategia przechowywania plików,
- przetwarzanie synchroniczne lub asynchroniczne,
- REST lub komunikacja asynchroniczna,
- wykorzystanie Service Bus,
- projekt integracji AI,
- prompty,
- architektura RAG,
- magazyn wektorowy,
- dzielenie na fragmenty,
- model autoryzacji,
- mechanizmy niezawodności.

Ważne decyzje należy zapisywać w `DECISIONS.md`.

---

# 16. Wytyczne dla Recenzenta

Recenzent ocenia implementację względem **bieżącej wersji projektu**, a nie wyobrażonej architektury docelowej.

Recenzent powinien zapytać:
1. Czy implementacja spełnia bieżące wymagania biznesowe?
2. Czy kryteria akceptacji są spełnione?
3. Czy niezmienniki biznesowe są wymuszane?
4. Czy rozwiązanie jest niepotrzebnie złożone?
5. Czy wprowadzono jakąkolwiek technologię bez konkretnego wymagania?
6. Czy ważne decyzje są uzasadnione?
7. Czy funkcje późniejszych wersji są implementowane przedwcześnie?
8. Czy bieżący projekt tworzy poważny problem dla następnego znanego etapu?
9. Czy bieżące granice bezpieczeństwa są przestrzegane?
10. Czy deweloper rozumie implementację i bierze za nią odpowiedzialność?

Prawidłowe rozwiązanie V1 nie powinno zostać odrzucone dlatego, że nie zawiera jeszcze mechanizmów V7/V8.

---

# 17. Wstępne założenia implementacyjne

> Zbuduj zaplecze systemu, w którym użytkownik może utworzyć wniosek biznesowy, przekazać go do przeglądu, a inny użytkownik może go zatwierdzić lub odrzucić. System musi wymuszać prawidłowe przejścia stanów i zachowywać historię ważnych operacji.

Określa to wymagane zachowanie. Deweloper decyduje, jak rozwiązanie zostanie zamodelowane i zaimplementowane.
