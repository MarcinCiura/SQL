## LABORATORIUM 7

Na tym laboratorium znów będziemy korzystać z bazy danych
o składnikach potraw.

### Zadania

Proszę wziąć kartkę i ołówek (może też być długopis :-)
Proszę zapisać na kartce poniższe instrukcje SQL.

#### Zadanie 1: Tworzenie indeksu (`CREATE INDEX`)

W bazie danych często wyszukuje się składniki po ich nazwie. Utwórz
indeks na kolumnie `nazwa` w tabeli ze składnikami, aby przyspieszyć
wykonywanie zapytań wyszukujących lub sortujących składniki według
nazwy.

#### Zadanie 2: Usuwanie indeksu (`DROP INDEX`)

Usuń z bazy danych utworzony wcześniej indeks.

#### Zadanie 3: Tworzenie widoku (`CREATE VIEW`)

Utwórz widok o nazwie `szczegoly_przepisow`, który połączy dane
z tabel o potrawach, o składnikach i o składnikach potraw. Ten widok
powinien wyświetlać:

* nazwę potrawy jako `potrawa`,

* nazwę składnika jako `skladnik`,

* ilość składnika jako `miara`,

* łączną kaloryczność danego składnika w potrawie jako `kaloryczność`.

Sprawdź, czy widok działa, za pomocą zapytania `SELECT * FROM...`

#### Zadanie 4: Zapytanie do widoku

Znajdź wszystkie składniki wszystkich potraw wraz z ich
kalorycznością. Skorzystaj z utworzonego wcześniej widoku.

#### Zadanie 5: Funkcja `ROW_NUMBER`

Napisz zapytanie do utworzonego wcześniej widoku, które wykorzysta
funkcję okienkową `ROW_NUMBER`, aby ponumerować składniki potraw.

### Jak rozwiązywać zadania?

- Proszę uruchomić program `sqlite3` z argumentem `potrawy.sqlite3`:
```bash
sqlite3 potrawy.sqlite3
```

- Proszę przepisać z kartki instrukcje i zapytania SQL. Proszę
pamiętać o zakończeniu każdej instrukcji i każdego zapytania
średnikiem `;`

- Jeśli jakaś instrukcja lub zapytanie SQL zakończy się błędem, proszę
powoli i dokładnie przeczytać komunikat o błędzie i przepisać
tę instrukcję lub zapytanie jeszcze raz. Można też użyć:

    - klawisza "strzałka w górę", aby powtórnie edytować poprzednią
      linię
    - klawisza "strzałka w lewo" lub "strzałka w prawo", aby przesuwać
      kursor
    - klawisza "Backspace", aby skasować znak na lewo od kursora
    - kombinacji klawiszy "Ctrl+A" lub "Ctrl+E", aby przenieść kursor
      na początek lub na koniec linii.

- Jeśli ktoś nie potrafi poprawić jakiejś instrukcji lub jakiegoś
zapytania SQL, niech poprosi o pomoc sąsiada, sąsiadkę lub
prowadzącego :-)

- W razie błędów proszę poprawiać instrukcje i zapytania SQL zapisane
na kartce, aby były takie same jak poprawnie działające instrukcje
i zapytania wpisane do programu `sqlite3`
