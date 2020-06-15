# Implemented functions and some examples of their use

When you start, you have an empty database.

1. Create table
2. Insert rows
3. Update or delete some rows
4. Search for information using the SELECT query

Example
```
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('nauris', 8);
UPDATE Tuotteet SET hinta=14 WHERE nimi='banaani';
DELETE FROM Tuotteet WHERE hinta<=7;
SELECT * FROM Tuotteet ORDER BY hinta;
```
![pic01.png](pic01.png)


## Arithmetic Operators (+, -, *, /, %)

```
CREATE TABLE Example (id INTEGER);
INSERT INTO Example (id) VALUES (1);
SELECT 11+4, 11-4, 11*4, 11/4, 11%4, 4-1*3+10/2 FROM Example;
```
![pic02.png](pic02.png)


## String Functions
```
LENGTH  Returns the length of a string
```
```
CREATE TABLE Example (id INTEGER, month TEXT);
INSERT INTO Example (id, month) VALUES (1, 'January');
INSERT INTO Example (id, month) VALUES (6, 'June');
SELECT month, LENGTH(month) FROM Example ORDER BY month DESC;
```
![pic03.png](pic03.png)

## Math/Numeric Functions

```
AVG    Returns the average value of an expression
COUNT  Returns the number of records returned by a select query
MAX    Returns the maximum value in a set of values
MIN    Returns the minimum value in a set of values
SUM    Calculates the sum of a set of values
```

```
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 4);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 3);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 2);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('nauris', 1);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('bucket', 0);
SELECT SUM(hinta)/COUNT(*) FROM Tuotteet;
```
![pic04.png](pic04.png)

## Comparison Operators

```
=	Equal to
>	Greater than
<	Less than
>=	Greater than or equal to
<=	Less than or equal to
<>	Not equal to
```

## Logical Operators

```
AND   TRUE if all the conditions separated by AND is TRUE
OR    TRUE if any of the conditions separated by OR is TRUE
```

```
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 4);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('nauris', 4);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('bucket', 0);
SELECT nimi, hinta, 5*hinta+3, LENGTH(nimi) FROM Tuotteet WHERE hinta=LENGTH(nimi) OR (hinta+1=5 AND nimi<>'banaani') OR (hinta=2*hinta) ORDER BY LENGTH(hinta), hinta;
```
![pic05.png](pic05.png)