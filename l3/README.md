## LABORATORIUM 3

Od dziś na zajęciach będziemy korzystać z bazy danych Sakila. Sakila
to przykładowa relacyjna baza danych stworzona przez firmę MySQL AB
(obecnie należącą do Oracle), zaprojektowana specjalnie do celów
edukacyjnych, testowych i demonstracyjnych. Sakila modeluje działanie
wypożyczalni kaset wideo i DVD.

### Struktura bazy danych Sakila

Baza danych Sakila składa się z 16 powiązanych ze sobą tabel, które
odzwierciedlają realia prowadzenia wypożyczalni filmów:

- Zarządzanie filmami: `film`, `actor`, `film_actor`, `category`,
`film_category`, `film_text`, `language`

- Inwentarz i placówki: `inventory`, `store`, `staff`

- Klienci i transakcje: `customer`, `rental`, `payment`

- Geografia i dane adresowe: `address`, `city`, `country`

Schemat zawiera również gotowe widoki (views): `film_list`,
`actor_info`, `staff_list`, `customer_list`, `sales_by_store`,
`sales_by_film_category`. Te widoki ułatwiają analizę danych bez
pisania skomplikowanych agregacji.

![Struktura bazy danych Sakila](../sakila.png)

### Zadania

Proszę wziąć kartkę i ołówek (może też być długopis :-)
Proszę zapisać na kartce poniższe zapytania SQL.

#### Zadanie 1: Operator równości (`=`)

Wyświetl tytuł (`title`) oraz kategorię wiekową (`rating`) wszystkich
filmów z tabeli `film`, których kategoria wiekowa to `'PG'`.

#### Zadanie 2: Operator nierówności (`<>`)

Znajdź imiona (`first_name`) i nazwiska (`last_name`) klientów
z tabeli `customer`, którzy są przypisani do sklepu innego niż sklep
o `store_id` równym `1`.

#### Zadanie 3: Operator mniejszości (`<`)

Wyświetl tytuły filmów (`title`) oraz ich koszt zastąpienia
(`replacement_cost`) z tabeli `film`, dla których koszt ten jest
mniejszy niż `15.00`.

#### Zadanie 4: Operator większości (`>`)

Wyświetl identyfikatory płatności (`payment_id`) oraz ich kwoty
(`amount`) z tabeli `payment`, w których kwota transakcji była większa
niż `10.00`.

#### Zadanie 5: Operator mniejsze lub równe (`<=`)

Wyświetl tytuł (`title`) oraz dopuszczalny okres wypożyczenia
(`rental_duration`) z tabeli `film` dla filmów, których czas
wypożyczenia wynosi maksymalnie 3 dni.

#### Zadanie 6: Operator większe lub równe (`>=`)

Znajdź tytuły (`title`) i czas trwania (`length`) filmów z tabeli
`film`, których czas trwania wynosi co najmniej 180 minut.

#### Zadanie 7: Weryfikacja braku wartości (`IS NULL`)

Z tabeli `rental` wypisz identyfikatory wypożyczeń (`rental_id`) oraz
daty wypożyczenia (`rental_date`) dla egzemplarzy, które nie zostały
jeszcze zwrócone (pole `return_date` ma wartość `NULL`).

#### Zadanie 8: Weryfikacja obecności wartości (`IS NOT NULL`)

Wyświetl identyfikatory wypożyczeń (`rental_id`) oraz daty zwrotu
(`return_date`) z tabeli `rental` dla wszystkich egzemplarzy, które
zostały już zwrócone do wypożyczalni (pole `return_date` ma przypisaną
wartość, czyli nie jest `NULL`).

#### Zadanie 9: Logiczny spójnik `AND`

Wyświetl tytuł (`title`), czas trwania (`length`) oraz ocenę wiekową
(`rating`) filmów z tabeli `film`, które trwają dłużej niż 120 minut
ORAZ posiadają kategorię wiekową `'PG-13'`.

#### Zadanie 10: Logiczny spójnik `OR`

Znajdź imię (`first_name`) i nazwisko (`last_name`) klientów z tabeli
`customer`, których nazwisko to `'SMITH'` LUB `'WILLIAMS'`.

#### Zadanie 11: Operator negacji `NOT`

Wybierz tytuły (`title`) i koszty zastąpienia (`replacement_cost`)
filmów z tabeli `film`, które NIE kosztują więcej niż 15.00.

#### Zadanie 12: Zakres wartości `BETWEEN ... AND`

Wyświetl tytuł (`title`) oraz czas trwania (`length`) filmów z tabeli
`film`, których długość mieści się w przedziale od 90 do 120 minut
(włącznie).

#### Zadanie 13: Dopasowanie do listy `IN`

Znajdź tytuły (`title`) oraz kategorie wiekowe (`rating`) filmów
z tabeli `film`, których kategoria wiekowa należy do zbioru: `'G'`,
`'PG'` lub `'NC-17'`.

#### Zadanie 14: Wyszukiwanie wzorca `LIKE`

Wyświetl tytuły filmów (`title`) z tabeli `film`, które zawierają
ciąg znaków `'STRANGER'`.

#### Zadanie 15: Połączenie dwóch tabel

Wyświetl nazwę miasta (`city`) oraz odpowiadającą mu nazwę kraju
(`country`), łącząc tabele `city` i `country`. Ogranicz wyniki tylko
do miast leżących w kraju `'Poland'`.

#### Zadanie 16: Połączenie dwóch tabel

Wybierz imię (`first_name`), nazwisko (`last_name`) oraz adres
(`address`) wszystkich aktywnych klientów (`active = '1'`), łącząc
tabele `customer` oraz `address`.

#### Zadanie 17: Połączenie dwóch tabel

Wyświetl tytuł filmu (`title`) oraz nazwę języka (`name`), w jakim
został nakręcony, dla wszystkich filmów, których opłata
za wypożyczenie (`rental_rate`) wynosi `0.99`.

#### Zadanie 18: Wielokrotne łączenie tabel

Pobierz tytuły filmów (`title`) oraz daty ich wypożyczenia
(`rental_date`) dla klientki o imieniu `'MARY'` i nazwisku `'SMITH'`.
Wymaga to połączenia tabel `customer`, `rental`, `inventory` i `film`.

#### Zadanie 19: Wielokrotne łączenie tabel

Wyświetl tytuł filmu (`title`), imię (`first_name`) i nazwisko
(`last_name`) aktora dla wszystkich filmów z kategorii `'Action'`.
Połącz ze sobą tabele `category`, `film_category`, `film`,
`film_actor` oraz `actor`.

#### Zadanie 20: Łączenie `JOIN ... ON` z kluczami o różnych nazwach

Znajdź identyfikator płatności (`payment_id`), kwotę (`amount`),
e-mail klienta (`email`) oraz imię i nazwisko menedżera sklepu
(`manager_staff_id`), w którym dokonano płatności. Warunki:

* Tabela `store` musi zostać połączona z tabelą `staff` za pomocą `ON
  store.manager_staff_id = staff.staff_id` (ze względu na różne nazwy
  kluczy).

* Wyświetl tylko transakcje o kwocie (`amount`) większej niż `10.00`.

#### Zadanie 21: Instrukcja ALTER TABLE

- Proszę znaleźć bazę danych `potrawy.sqlite3` z laboratorium 2.

- Proszę wykonać polecenie
```bash
sqlite3 potrawy.sqlite3 .dump > potrawy.sql
```

- Proszę otworzyć plik `potrawy.sql` w dowolnym edytorze tekstu, aby
  przypomnieć sobie rozwiązanie zadania z laboratorium 2.

- Proszę napisać na kartce instrukcję, która doda kolumnę `kcal`
  (kilokalorie) do tabeli ze składnikami potraw. Służy do tego
  instrukcja `ALTER TABLE`.

#### Zadanie 22: Instrukcja UPDATE

- Proszę napisać na kartce instrukcje, które uzupełnią kaloryczność
  składników w tabeli ze składnikami potraw zgodnie z tą listą:

    - dowolna ilość wody: 0

    - 1 szklanka mleka 2%: 125

    - 1 szklanka mąki pszennej: 550

    - 1 jajko rozmiaru M: 75

    - szczypta soli: 0

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

- Proszę uruchomić program `sqlite3` z argumentem `potrawy.sqlite3`:
```bash
sqlite3 potrawy.sqlite3
```
i przepisać rozwiązania zadań 21 i 22. W razie błędów proszę poprawić
rozwiązania na kartce.

- Proszę wyjść z programu `sqlite3` instrukcją `.quit`

- Proszę podpisać kartkę i oddać ją prowadzącemu :-)
