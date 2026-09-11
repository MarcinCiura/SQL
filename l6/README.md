## LABORATORIUM 6

![Struktura bazy danych Sakila](../sakila.png)

### Zadania

Proszę wziąć kartkę i ołówek (może też być długopis :-)
Proszę zapisać na kartce poniższe zapytania SQL.

#### Zadanie 1: Połączenie zbiorów z usunięciem duplikatów (`UNION`)

Pobierz listę wszystkich imion (`first_name`) i nazwisk (`last_name`)
osób występujących w bazie danych jako aktorzy w tabeli `actor` lub
jako klienci w tabeli `customer`. Użyj operatora `UNION`, aby usunąć
powtarzające się kombinacje imion i nazwisk.

#### Zadanie 2: Połączenie zbiorów z zachowaniem duplikatów (`UNION ALL`)

Stwórz zestawienie wszystkich imion (`first_name`) i nazwisk
(`last_name`) osób z tabeli `staff` oraz z tabeli `customer`, dodając
kolumnę `rola` z wartością `'Pracownik'` lub `'Klient'` określającą
ich rolę w systemie. Użyj operatora `UNION ALL`, aby połączyć dane bez
sprawdzania i usuwania powtórzeń.

#### Zadanie 3: Część wspólna zbiorów (`INTERSECT`)

Znajdź zestawienie tych imion (`first_name`) i nazwisk (`last_name`),
które występują **zarówno** w tabeli `actor`, jak i w tabeli
`customer` (osoby noszące te same dane w obu tabelach). Użyj operatora
`INTERSECT`.

#### Zadanie 4: Różnica zbiorów (`EXCEPT`)

Wyświetl pary imienia (`first_name`) i nazwiska (`last_name`) z tabeli
`actor`, które **nie występują** w tabeli `customer` (czyli dane
aktorów, których nie nosi żaden z klientów). Użyj operatora `EXCEPT`.

#### Zadanie 5: Proste CTE z agregacją i złączeniem (`WITH ... AS`)

Napisz zapytanie z wykorzystaniem klauzuli `WITH`, które wyznaczy
łączny przychód z wypożyczeń dla każdego filmu. W tabeli tymczasowej
(CTE) oblicz sumę wpłat (`SUM(amount)`) przypisaną do poszczególnych
filmów na podstawie tabel `payment`, `rental` oraz `inventory`.

Zgłoś wynik w zapytaniu głównym, wyświetlając tytuł filmu (`title`),
wyliczony przychód oraz kategorię wiekową (`rating`). Filtruj wyniki
tak, aby pokazać jedynie filmy o ocenie `'PG-13'`, których łączny
przychód przekroczył `100.00`.

#### Zadanie 6: Porównanie ze średnią w ramach tej samej grupy

Wyświetl tytuł (`title`), kategorię wiekową (`rating`) oraz czas
trwania (`length`) dla filmów z tabeli `film`, których czas trwania
jest większy niż średnia długość wszystkich filmów posiadających
**tę samą kategorię wiekową** (`rating`). Użyj podzapytania
skorelowanego, połączonego po kolumnie `rating`.

#### Zadanie 7: Wyszukiwanie wartości ekstremalnych dla każdego rekordu nadrzędnego

Z tabeli `payment` pobierz identyfikator płatności (`payment_id`),
identyfikator klienta (`customer_id`), kwotę (`amount`) oraz datę
płatności (`payment_date`). Wyświetl tylko te płatności, które
stanowią **najwyższą pojedynczą kwotę transakcji** zarejestrowaną dla
danego klienta. Wykorzystaj podzapytanie skorelowane po kluczu
`customer_id`.

#### Zadanie 8: Podzapytanie z operatorem `IN`

Wyświetl tytuły (`title`) oraz opłatę za wypożyczenie (`rental_rate`)
wszystkich filmów z tabeli `film`, które należą do kategorii
`'Comedy'`. Użyj podzapytania z operatorem `IN` wyciągającego
identyfikatory filmów z tabeli łączącej `film_category` dla danej
nazwy kategorii z tabeli `category`.

#### Zadanie 9: Podzapytanie skorelowane z operatorem `EXISTS`

Wyświetl imiona (`first_name`), nazwiska (`last_name`) oraz adresy
e-mail (`email`) tych klientów z tabeli `customer`, którzy
przynajmniej raz wypożyczyli film trwający ponad 180 minut.
Wykorzystaj podzapytanie skorelowane łączące tabele `rental`,
`inventory` oraz `film` w klauzuli `EXISTS`. Zacznij podzapytanie
od `SELECT 1`.

#### Zadanie 10: Podzapytanie skorelowane z operatorem `NOT EXISTS`

Znajdź imiona (`first_name`) oraz nazwiska (`last_name`) tych klientów
z tabeli `customer`, którzy nigdy nie dokonali pojedynczej płatności
(tabela `payment`) na kwotę większą niż `10.00`. Wykorzystaj
podzapytanie skorelowane z operatorem `NOT EXISTS`. Zacznij
podzapytanie od `SELECT 1`.

#### Zadanie 11: Podzapytanie w klauzuli `FROM` (tabela pochodna)

Wyświetl imię (`first_name`), nazwisko (`last_name`) oraz łączną
liczbę wypożyczeń dla klientów z tabeli `customer`, którzy dokonali
więcej niż 35 wypożyczeń. Liczbę wypożyczeń dla poszczególnych
klientów oblicz w podzapytaniu umieszczonym w klauzuli `FROM`.

#### Zadanie 12: Podzapytanie w klauzuli `SELECT` (podzapytanie skalarne)

Dla filmów z tabeli `film` o kategorii wiekowej `'PG'` wyświetl tytuł
(`title`) oraz — za pomocą skorelowanego podzapytania umieszczonego
bezpośrednio w klauzuli `SELECT` — oblicz łączną liczbę aktorów
grających w danym filmie na podstawie tabeli `film_actor`. Posortuj
wyniki malejąco według obliczonej liczby aktorów.

### Jak rozwiązywać zadania?

- Proszę uruchomić program `sqlite3` z argumentem `sakila.sqlite3`:
```bash
sqlite3 sakila.sqlite3
```

- Proszę przepisać z kartki zapytania SQL. Polecam nie używać klawisza
ENTER wewnątrz zapytań. Dzięki temu łatwiej będzie można je edytować,
używając klawisza "strzałka w górę". Proszę pamiętać o zakończeniu
każdego zapytania średnikiem `;`

- Jeśli jakieś zapytanie zakończy się błędem, proszę powoli
i dokładnie przeczytać komunikat o błędzie i przepisać to zapytanie
jeszcze raz. Można też użyć:

    - klawisza "strzałka w górę", aby powtórnie edytować poprzednią
      linię
    - klawisza "strzałka w lewo" lub "strzałka w prawo", aby przesuwać
      kursor
    - klawisza "Backspace", aby skasować znak na lewo od kursora
    - kombinacji klawiszy "Ctrl+A" lub "Ctrl+E", aby przenieść kursor
      na początek lub na koniec linii.

- Jeśli ktoś nie potrafi poprawić jakiegoś zapytania, niech poprosi
o pomoc sąsiada, sąsiadkę lub prowadzącego :-)

- W razie błędów proszę poprawiać zapytania zapisane na kartce, aby
były takie same jak poprawnie działające zapytania wpisane
do programu `sqlite3`.

- Proszę wyjść z programu `sqlite3` instrukcją `.quit`

- Proszę podpisać kartkę i oddać ją prowadzącemu :-)
