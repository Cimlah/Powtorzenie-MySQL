# Powtórzenie MySQL

## Podział na grupy
### DDL - Data Definition Language
* Create *database* | *table*
  ``` SQL
  CREATE table(
    cell1 int,
    cell2 varchar
  );
  ```
* Alter *table*
  ``` SQL
  ALTER TABLE uczniowie
  ADD COLUMN pseudonim AFTER imie;
  ```

  ``` SQL
  ALTER TABLE uczniowie
  CHANGE COLUMN pseudonim ksywka varchar(20);
  ```
* Drop *database* | *table* | *column*

### DML - Data Manipulation Language
* Insert
  ``` SQL
  INSERT INTO table(cell1, cell2) VALUE(value1, value2);
  ```
* Select
  ``` SQL
  SELECT * FROM table;
  ```

  ``` SQL
  SELECT DISTINCT cell FROM table;
  ```
* Update
  ``` SQL
  UPDATE uczniowie SET imie "AAA" WHERE imie = "AAAA";
  ```
* Delete
  ``` SQL
  DELETE FROM uczniowie WHERE condition;
  ```

### DCL - Data Controll Language
* Grant
* Revoke

## Inne polecenia
* Show *table*
* Describe *table*

## Typy danych
### Liczbowe
* Int < -2mld; 2mld >
* Tinyint 1B < -127; 128 >
* Smallint 2B < -32000; 32000 >
* Mediumint 3B < -8mln; 8mln >
* Bigint 8B < -pow(2, 63); pow(2, 63) >
* Float - zmiennoprzecinkowe
* Double - zmiennoprzecinkowe
* Decimal
### Tekstowe
* Char
* Varchar
* Tinytext - 255 znaków
* Text - 65535 znaków
* Mediumtext - 16mln znaków
* Longtext - 4mld znaków
### Czas/data
* Date - *YYYY*-*MM*-*DD*
* Datetime - *YYYY*-*MM*-*DD* *HH*:*MM*:*SS*
* Time *HH*:*MM*:*SS*
### Inne
* Enum - typ wyliczeniowy *(wart1, wart2, wart3)*
* Boolean - logiczny *true* albo *false*
* Unsigned *int* - przed typem danych sprawia, że będą tylko wartości nieujemne (czyli >= 0)

## Parametry komórek
* PRIMARY KEY - klucz główny
* AUTO_INCREMENT - automatyczna inkrementacja
* NOT NULL - nie może być puste
* UNIQUE - unikatowa, niepowtarzająca się wartość
* DEFAULT - wartość domyślna
* CHECK - sprawdzenie warunku (np. wiek > 18)

## Operatory w `WHERE`
* *>=* - większe lub równe
* *<=* - mniejsze lub równe
* *=* - równe
* *<>* - nierówne
* OR - lub
* AND - i
* IN(*value1*, *value2*, *value3*) - wyszukuje w podanym zbiorze
* BETWEEN *value1* AND *value2* - wyszukuje w podanym zbiorze liczbowym
* NOT - zaprzeczenie, negacja
* LIKE - porównuje ze wzorcem
  * % - dowolna ilość znaków
  * _ - maskuje jeden znak
* IS (NOT) NULL - sprawdza czy pole (nie) jest puste

## Sortowanie
`ORDER BY` służy do sortowania.

``` SQL
SELECT name
FROM names
ORDER BY name ASC;
```

* ASC - sortowanie rosnąco
* DESC - sortowanie malejąco

## Grupowanie
`GROUP BY` służy do grupowania

``` SQL
SELECT name
FROM names
GROUP BY name;
```

## Inne funkcje
* COUNT(*column*) - liczy ilość komórek w kolumnie
* MIN - wybiera najmniejszą wartość z kolumny
* MAX - wybiera największą wartość z kolumny
* SUM - sumuje wartości z kolumny
* AVG - oblicza średnią z kolumny
* HAVING - filtrowanie po grupowaniu (po grupowaniu nie można użyć `WHERE`)
* LIMIT *number* - limituje ilość zwróconych rekordów

## Widok
Widok jest wykorzystywany jako wirtualna tabela.
``` SQL
CREATE VIEW view1 AS SELECT value1, value2 FROM table;
```

## Kontrola dostępu
### Utworzenie użytkownika
``` SQL
CREATE USER user1@localhost IDENTIFIED BY "password";
```

### Usunięcie użytkownika
``` SQL
DROP USER user1@localhost;
```

### Lista uprawnień
* ALL PRIVILAGES - wszystkie uprawnienia
* ALTER - modyfikacja struktury tabeli
* CREATE - tworzenie obiektów
* DELETE - usuwanie danych
* DROP - usuwanie tabel
* SELECT - przeglądanie danych
* UPDATE - zmiana danych
* USAGE - przeglądanie danych
* SHOW *database* | *table* - przeglądanie baz danych i tabeli na serwerze

#### GRANT - nadaje uprawnienia
``` SQL
GRANT SELECT(column) ON database.table
TO user1@localhost;
```
#### REVOKE - zabiera uprawnienia
``` SQL
REVOKE SELECT(column) ON database.table
FROM user1@localhost;
```
#### SET PASSWORD
``` SQL
SET PASSWORD FOR user1@localhost=PASSWORD("1234");
```