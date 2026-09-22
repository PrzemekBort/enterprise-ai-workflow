# Dziennik nauki
---
### 21.09.2026 E0S0
Nauka — czego się dowiedziałem:			
Budowanie — co zrobiłem w projekcie:	Samodzielne powtórzenie ćwiczeń
										uruchomienie - docker start [nazwa]
										logi (ostatnie 30) - docker logs --tail 30 [nazwa]
										sprawdzenie działania - docker exec [nazwa] psql -U postgres -d eaw_lab -c [zapytanie]
										restart - docker restart [nazwa]
										stop - docker stop [nazwa]
										Stan Up mówi o działającym kontenerze anie gotowosci jego składników wewnątrz
										Git, .NET, Python i Docker były dostępne i odpowiedziały na polecenia wersji.
										
Problem / luka:							Nie
Czy luka blokuje etap?					Nie
Pomoc AI:								Komenda do zmiany nazwy kontenera "docker [nazwa] [nowa_nazwa]"
Co zrobiłem samodzielnie:				Git, Docker: Wykonanie komend z AI
Następny krok:							

---
### 21.09.2026 E0S0
Nauka — czego się dowiedziałem:			Git: Jak zrobic branch i merge. Jesli w main nie było zmian po branchu to następuje fast-forward czyli przesunięcie main na koniec gałezi. 
											Commit miał dwóch rodziców ponieważ po branchu na obu gałęziać wystąpiły niezależne zmiany
										Docker: Up potwierdza działanie procesu kontenra ale nie jego składników wewnatrz, to potwierdzają np. logi a w przypadku postgres poprawnnie wykonany select
											Docker Engine działał, kontener eaw-postgres-lab miał status Up, logi potwierdziły gotowość PostgreSQL, a SELECT 1 zakończył się powodzeniem przed i po restarcie.
Budowanie — co zrobiłem w projekcie:	Git: Wykonanie branch i merge
Problem / luka:							Git: Obsługa konfliktów  
Czy luka blokuje etap?					Git: Nie  
Pomoc AI:								Git, Docker: Wyjaśnienie pojęć oraz komendy  
Co zrobiłem samodzielnie:				Git, Docker: Wykonanie komend z AI
Następny krok:							Samodzielnie powtórzyć podstawową weryfikację Docker/PostgreSQL bez podanych komend.
