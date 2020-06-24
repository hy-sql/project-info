# Implemented features and some examples of their use

When you start, you have an empty database.

1. Create table
2. Insert rows
3. Update or delete some rows
4. Search for information using the SELECT query

Example: <https://hy-sql.netlify.app/>

```sql
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('nauris', 8);
UPDATE Tuotteet SET hinta=14 WHERE nimi='banaani';
DELETE FROM Tuotteet WHERE hinta<=7;
SELECT * FROM Tuotteet ORDER BY hinta;
```

![pic01.png](https://github.com/hy-sql/project-info/blob/master/documents/examples/pic01.PNG)

## Arithmetic Operators (+, -, \*, /, %)

```sql
CREATE TABLE Example (id INTEGER);
INSERT INTO Example (id) VALUES (1);
SELECT 11+4, 11-4, 11*4, 11/4, 11%4, 4-1*3+10/2 FROM Example;
```

![pic02.png](https://github.com/hy-sql/project-info/blob/master/documents/examples/pic02.PNG)

## String Functions

```text
LENGTH  Returns the length of a string
```

```sql
CREATE TABLE Example (id INTEGER, month TEXT);
INSERT INTO Example (id, month) VALUES (1, 'January');
INSERT INTO Example (id, month) VALUES (6, 'June');
SELECT month, LENGTH(month) FROM Example ORDER BY month DESC;
```

![pic03.png](https://github.com/hy-sql/project-info/blob/master/documents/examples/pic03.PNG)

## Math/Numeric Functions

```text
AVG    Returns the average value of an expression
COUNT  Returns the number of records returned by a select query
MAX    Returns the maximum value in a set of values
MIN    Returns the minimum value in a set of values
SUM    Calculates the sum of a set of values
```

```sql
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 4);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 3);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 2);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('nauris', 1);
SELECT AVG(hinta), COUNT(*), MAX(hinta), MIN(hinta), SUM(hinta) FROM Tuotteet;
```

![pic04.png](https://github.com/hy-sql/project-info/blob/master/documents/examples/pic04.PNG)

## Comparison Operators

```text
=   Equal to
>   Greater than
<   Less than
>=  Greater than or equal to
<=  Less than or equal to
<>  Not equal to
```

## Logical Operators

```text
AND   TRUE if all the conditions separated by AND is TRUE
OR    TRUE if any of the conditions separated by OR is TRUE
```

## Example of Comparison Operators and Logical Operators

```sql
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('banaani', 4);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('nauris', 4);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('bucket', 0);
SELECT nimi, hinta, 5*hinta+3, LENGTH(nimi)
FROM Tuotteet
WHERE hinta=LENGTH(nimi) OR (hinta+1=5 AND nimi<>'banaani') OR (hinta=2*hinta)
ORDER BY LENGTH(hinta), hinta;
```

![pic05.png](https://github.com/hy-sql/project-info/blob/master/documents/examples/pic05.PNG)

## Example of GROUP BY with HAVING

```sql
CREATE TABLE Tehtavat (id INTEGER PRIMARY KEY, tarkeys INTEGER, projekti_id INTEGER);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (2, 4);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (3, 4);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (3, 3);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (4, 3);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (1, 2);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (3, 2);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (3, 2);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (4, 1);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (4, 1);
INSERT INTO Tehtavat (tarkeys, projekti_id) VALUES (4, 1);
SELECT projekti_id, COUNT(*)
FROM Tehtavat
WHERE tarkeys >= 3
GROUP BY projekti_id
HAVING COUNT(*) >= 2
ORDER BY projekti_id;
```

| project_id | COUNT(\*) |
| ---------- | --------- |
| 1          | 3         |
| 2          | 2         |
| 3          | 2         |

## Example of LIMIT

```sql
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('omena', 5);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('kirsikka', 8);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 3);
SELECT nimi, hinta FROM Tuotteet ORDER BY hinta LIMIT 2;
```

|   nimi   | hinta |
| -------- | ----- |
| porkkana | 3     |
| omena    | 5     |


## Example of LIMIT OFFSET

```sql
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('omena', 5);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('kirsikka', 8);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 3);
SELECT nimi, hinta FROM Tuotteet ORDER BY hinta LIMIT 2 OFFSET 2;
```

|   nimi   | hinta |
| -------- | ----- |
| retiisi  | 7     |
| kirsikka | 8     |

## Example of DISTINCT

```sql
CREATE TABLE Tuotteet (id INTEGER PRIMARY KEY, nimi TEXT, hinta INTEGER);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('retiisi', 7);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 8);
INSERT INTO Tuotteet (nimi, hinta) VALUES ('porkkana', 3);
SELECT DISTINCT nimi, hinta FROM Tuotteet;
```
|   nimi   | hinta |
| -------- | ----- |
| retiisi  | 7     |
| porkkana | 8     |
| porkkana | 3     |
