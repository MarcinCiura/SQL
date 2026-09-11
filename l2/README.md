## LABORATORIUM 2

1. Proszę wziąć kartkę i ołówek (może też być długopis :-). Proszę
zaprojektować bazę danych o listach składników przepisów kulinarnych.
W naszej bazie danych będą dane o takich potrawach, które można
przyrządzić z wody, mleka, mąki, jajek i soli. Jest ich całkiem sporo.
Polecam artykuł Ryana Moultona *[The Hunt for Dark
Breakfast](https://moultano.wordpress.com/2026/02/22/the-hunt-for-dark-breakfast/)*.

Oto przykładowe listy składników:

Składniki na naleśniki:

- 0,5 szklanki wody
- 0,5 szklanki mleka
- 1 szklanki mąki
- 2 jajka
- 1 szczypta soli

Składniki na makaron:

- 1 łyżka wody
- 2 szklanki mąki
- 2 jajka
- 1 szczypta soli

Proszę tak zaprojektować tę bazę danych, aby użytkownik mógł się
z niej dowiedzieć, ile czego użyć przy przyrządzaniu każdej potrawy.
Proszę użyć w tej bazie danych kilku tabel. Dopuszczalna jest taka
tabela, w której będą osobne wiersze na ten sam składnik mierzony
w różnych jednostkach, na przykład:

|---------------|
| szklanka wody |
|---------------|
| łyżka wody    |
|---------------|

Aby rozwiązać to zadanie:

- proszę wyłączyć komputer (można wyłączyć tylko monitor :-)

- proszę dobrać się w pary (jeśli liczba uczestników jest nieparzysta,
dołącza do nich prowadzący)

- niech jedna osoba z pary przeprowadzi wywiad o potrawach z drugą
osobą, tworząc schemat bazy danych

- potem niech te osoby, które przeprowadzały wywiad, przejdą na jedną
stronę sali, a te osoby, które udzielały wywiadu, przejdą na drugą
stronę sali

- potem proszę znów dobrać się w pary, ale inne, po jednej osobie
z obu stron sali

- potem niech te osoby, które udzielały wywiadu, przeprowadzą wywiad,
tworząc schemat bazy danych, a te osoby, które przeprowadzały wywiad,
udzielą wywiadu :-)

2. Proszę zapisać na kartce instrukcje SQL, tworzące bazę danych
o składnikach potraw

3. Proszę zapisać na kartce instrukcje SQL, dodające do tej bazy
danych listę składników na naleśniki i listę składników na makaron

4. Proszę:

- Włączyć komputer

- Uruchomić program `sqlite3` z argumentem `potrawy.sqlite3`:
```bash
sqlite3 potrawy.sqlite3
```

- Przepisać z kartki instrukcje SQL, tworzące bazę danych. Proszę
pamiętać o zakończeniu każdej instrukcji średnikiem `;`

- Jeśli jakaś instrukcja SQL zakończy się błędem, proszę powoli
i dokładnie przeczytać komunikat o błędzie i przepisać tę instrukcję
jeszcze raz. Można też użyć:

    - klawisza "strzałka w górę", aby powtórnie edytować poprzednią
      linię
    - klawisza "strzałka w lewo" lub "strzałka w prawo", aby przesuwać
      kursor
    - klawisza "Backspace", aby skasować znak na lewo od kursora
    - kombinacji klawiszy "Ctrl+A" lub "Ctrl+E", aby przenieść kursor
      na początek lub na koniec linii.

- Jeśli ktoś nie potrafi poprawić jakiejś instrukcji SQL, niech
poprosi o pomoc sąsiada, sąsiadkę lub prowadzącego :-)

- W razie błędów proszę poprawiać instrukcje SQL zapisane na kartce,
aby były takie same jak poprawnie działające instrukcje wpisane
do programu `sqlite3`

- Kiedy wszystkie składniki makaronu i wszystkie składniki naleśników
zostaną dodane do bazy danych, proszę to sprawdzić zapytaniami
`SELECT * FROM ...;`, a potem wyjść z programu `sqlite3` instrukcją
`.quit`

- Potem proszę znów uruchomić program `sqlite3` z argumentem
`potrawy.sqlite3`:
```bash
sqlite3 potrawy.sqlite3
```
i sprawdzić zapytaniami `SELECT * FROM ...;`, czy wszystkie składniki
makaronu i naleśników zostały dodane do bazy danych. Można użyć
klawisza "strzałka w górę" :-)

- Proszę wyjść z programu `sqlite3` instrukcją `.quit`

- Proszę **nie kasować** bazy danych `potrawy.sqlite3`. Ta baza danych
będzie jeszcze potrzebna.

- Proszę podpisać kartkę i oddać ją prowadzącemu :-)
