## LABORATORIUM 4

![Struktura bazy danych Sakila](../sakila.png)

### Zadania

Proszę wziąć kartkę i ołówek (może też być długopis :-)
Proszę zapisać na kartce poniższe zapytania SQL.

#### Zadanie 1: Operator `||` oraz podwójny cudzysłów `"`

Wyświetl połączenie imienia i nazwiska aktora w jedną kolumnę
o etykiecie `"Aktor (imię i nazwisko)"` (używając operatora `||`) oraz
tytuł filmu ujęty w kolumnę `"Tytuł filmu"`. Uwzględnij tylko filmy
z kategorią wiekową `'PG-13'`.

#### Zadanie 2: Funkcje agregujące `COUNT(*)` oraz `COUNT(kolumna)`

Oblicz łączną liczbę zarejestrowanych wypożyczeń (`COUNT(*)`) oraz
liczbę faktycznie zwróconych wypożyczeń (`COUNT(return_date)`) dla
klientki o imieniu `'EMILY'` i nazwisku `'DIAZ'`. Użyj podwójnych
cudzysłowów dla aliasów kolumn.

#### Zadanie 3: Funkcja agregująca `COUNT(DISTINCT kolumna)`

Policz, ilu **różnych aktorów** grało w filmach należących
do kategorii `'Action'`. Użyj `COUNT(DISTINCT ...)`.

#### Zadanie 4: Funkcje agregujące `SUM` oraz `AVG`

Oblicz łączną sumę wpłat (`SUM`) oraz średnią kwotę transakcji (`AVG`)
obsłużonych przez pracownika o imieniu `'Mike'`. Nadaj kolumnom
czytelne aliasy w podwójnych cudzysłowach.

#### Zadanie 5: Funkcje agregujące `MIN` oraz `MAX`

Znajdź najkrótszy (`MIN`) i najdłuższy (`MAX`) czas trwania filmu
(kolumna `length`), w którym zagrała aktorka `'PENELOPE GUINESS'`.

#### Zadanie 6: Liczba filmów w kategoriach

Wyświetl nazwy kategorii filmowych (`category.name`) oraz liczbę
filmów w każdej z nich (`COUNT(f.film_id)`) dla filmów, których opłata
za wypożyczenie (`rental_rate`) wynosi `0.99`.

#### Zadanie 7: Łączne wpłaty klientów u konkretnego pracownika

Znajdź imiona i nazwiska tych klientów (tabela `customer`), którzy
dokonali wpłat w transakcjach obsłużonych przez pracownika o `staff_id
= 1` na łączną kwotę przekraczającą `100.00`.

#### Zadanie 8: Aktorzy w filmach z wybraną kategorią wiekową

Wyświetl imiona i nazwiska tych aktorów (tabela `actor`), którzy
zagrali w więcej niż 10 filmach o kategorii wiekowej (`rating`) równej
`'NC-17'`.

#### Zadanie 9: Średnia długość i koszt zastąpienia filmów w kategoriach

Wyświetl nazwę kategorii (`category.name`) oraz średnią długość filmu
(`AVG(f.length)`) dla filmów z oceną `'G'` lub `'PG'`, których koszt
zastąpienia (`replacement_cost`) wynosi co najmniej `15.00`. Wypisz
tylko te kategorie, dla których średnia długość filmu jest większa niż
110 minut, a łączny koszt zastąpienia wszystkich spełniających warunek
filmów w tej kategorii przekracza `300.00`.

#### Zadanie 10: Niezwrócone wypożyczenia według krajów

Wyświetl nazwę kraju (`country.country`) oraz liczbę niezwróconych
wypożyczeń (gdzie `return_date IS NULL`) dokonanych przez aktywnych
klientów (`active = '1'`). Uwzględnij tylko te kraje, w których liczba
takich niezwróconych wypożyczeń wynosi co najmniej 3.

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
