vaade (view)

[Select laused](select.md) | [Kasutaja loomine XAMPP-is JA SQL Serveris](kasutaja.md) | [Triggerid](trigerid.md) | [Kodutöö - Keys](keys.md)  | [stored procedure](protseduurid.md) | [Enesetestid](Enesetestid_smlogitpe24.docx) | [Vaade](vaade.md)

Mis on vaade? Vaade (View) on virtuaalne tabel, mis põhineb SQL-päringul. Vaade ei salvesta andmeid ise  see on nagu "akna" kaudu vaatamine pärisandmetele. Iga kord, kui vaatele viidatakse, käivitatakse taustapäring uuesti.

Vaate loomine

CREATE VIEW vaate_nimi AS
SELECT veerg1, veerg2
FROM tabel
WHERE tingimus;
Vaade 1: Kõik brändid

CREATE VIEW kõik_brändid AS
SELECT * FROM Brands;
Kasutamine:

SELECT * FROM kõik_brändid;
Vaade 2: Brändid kategooriatega (JOIN)

CREATE VIEW brändid_kategooriatega AS
SELECT b.Brand_Name, c.Category_Name
FROM Brands b
JOIN Category c ON b.category_id = c.category_id;
Kasutamine:

SELECT * FROM brändid_kategooriatega;
Vaade 3: Ainult N-tähega brändid

CREATE VIEW n_brändid AS
SELECT Brand_Name FROM Brands
WHERE Brand_Name LIKE 'N%';
Kasutamine:
sqlSELECT * FROM n_brändid;
Vaate kustutamine

DROP VIEW vaate_nimi;
Vaate muutmine

kogu kood

CREATE VIEW koik_brandid AS
SELECT *
FROM Brands;

-- vaate 1 kasutamine
SELECT *
FROM koik_brandid;

-- vaate 2 loomine - brandid kategooriatega
CREATE VIEW brandid_kategooriatega AS
SELECT
    b.Brand_Name,
    c.Category_Name
FROM Brands b
JOIN Category c
ON b.category_id = c.category_id;

-- vaate 2 kasutamine
SELECT *
FROM brandid_kategooriatega;

-- vaate 3 loomine - n-tahega algavad brandid
CREATE VIEW n_brandid AS
SELECT Brand_Name
FROM Brands
WHERE Brand_Name LIKE 'N%';

-- vaate 3 kasutamine
SELECT *
FROM n_brandid;

-- vaate muutmine
ALTER VIEW n_brandid AS
SELECT Brand_Name
FROM Brands
WHERE Brand_Name LIKE 'S%';

-- kontroll
SELECT *
FROM n_brandid;

-- vaate kustutamine
DROP VIEW n_brandid;

ALTER VIEW vaate_nimi AS
SELECT ...uus päring...;
