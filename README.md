## Andmebaasid sandra magi portfoolio Logitpe24

Teemad
- [SELECT laused](select.md)
- [Kasutaja loomine SQL Serveris](kasutaja.md)
- [Primaar- ja välisvõtmed](keys.md)
- [Stored Procedures](protseduurid.md)
- [Triggerid](trigerid.md)
- [Enesetestid](Enesetestid_smlogitpe24.docx)
- [vaade](vaade.md)


SQL (Structured Query Language) on relatsiooniliste andmebaaside päringukeel.

DDL – Data Definition Language

Andmebaasi struktuuri loomiseks ja muutmiseks kasutatavad käsud:

CREATE
ALTER
DROP
DML – Data Manipulation Language

Andmete lisamiseks, muutmiseks ja kustutamiseks kasutatavad käsud:

INSERT
UPDATE
DELETE
Sisukord
Andmebaasihaldussüsteemid
Põhimõisted
Andmetüübid
Piirangud
Seosed
Stored Procedures
Andmebaasihaldussüsteemid
SQL Server Management Studio (SSMS)

Microsoft SQL Serveri andmebaaside haldamise keskkond.

XAMPP / phpMyAdmin

Vabavaraline keskkond MariaDB ja MySQL andmebaaside haldamiseks.

Põhimõisted
Andmebaas (Database)

Struktureeritud andmete kogum.

Tabel (Table)

Andmebaasi objekt, kuhu salvestatakse andmed.

Veerg (Column / Field)

Tabeli väli, mis kirjeldab andmeelementi.

Rida (Row / Record)

Üks kirje tabelis.

Primaarvõti (Primary Key, PK)

Veerg, mis sisaldab unikaalset identifikaatorit iga kirje jaoks.

Välisvõti (Foreign Key, FK)

Veerg, mis loob seose teise tabeli primaarvõtmega.

Andmetüübid
Numbrilised andmetüübid
INT
FLOAT
DECIMAL(6,2)
Tekstiandmetüübid
VARCHAR(50)
CHAR(6)
Loogilised andmetüübid
BOOLEAN
BOOL
BIT
Kuupäeva- ja kellaajatüübid
DATE
TIME
DATETIME
Piirangud (Constraints)
PRIMARY KEY
FOREIGN KEY
UNIQUE
NOT NULL
CHECK
Seosed
Üks ühele (1:1)

Näide:

inimene ↔ pass
Üks mitmele (1)

Näide:

õpetaja ↔ õpilased
Mitu mitmele (N)

Näide:

õpilane ↔ õppeained
Stored Procedures

Salvestatud protseduurid (Stored Procedures) on andmebaasi objektid, mis võimaldavad SQL-käske taaskasutada ja automatiseerida.

Neid kasutatakse näiteks:

andmete lisamiseks
andmete otsimiseks
andmete muutmiseks
andmete kustutamiseks
Uue kategooria lisamine
CREATE PROCEDURE lisaKategooria
    @nimi VARCHAR(15)
AS
BEGIN
    INSERT INTO Category
    VALUES (@nimi);

    SELECT * FROM Category;
END

Kasutamine:

EXEC lisaKategooria 'test'
Kategooria kustutamine ID järgi
CREATE PROCEDURE kustutaIDJargi
    @id INT
AS
BEGIN
    SELECT * FROM Category;

    DELETE FROM Category
    WHERE category_id = @id;

    SELECT * FROM Category;
END

Kasutamine:

EXEC kustutaIDJargi 3
Otsing esimese tähe järgi
CREATE PROCEDURE otsing1Taht
    @taht CHAR(1)
AS
BEGIN
    SELECT Category_Name
    FROM Category
    WHERE Category_Name LIKE @taht + '%';
END

Kasutamine:

EXEC otsing1Taht 'j'
Kategooria nime uuendamine
CREATE PROCEDURE uuendaKategooria
    @id INT,
    @uuendatudNimi VARCHAR(20)
AS
BEGIN
    SELECT * FROM Category;

    UPDATE Category
    SET Category_Name = @uuendatudNimi
    WHERE category_id = @id;

    SELECT * FROM Category;
END

Kasutamine:

EXEC uuendaKategooria 4, 'jope'

