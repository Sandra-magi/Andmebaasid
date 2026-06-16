## SQL Protseduurid (Stored Procedures)
Select laused | Protseduurid | vaade | Kasutaja | keys | küsimused | Triggerid

Mis on protseduur?
Protseduur (stored procedure) on eelkompileeritud SQL-lausete kogum, mis salvestatakse andmebaasi ja mida saab korduvalt käivitada. Protseduurid võtavad vastu parameetreid ja täidavad kindlaid toiminguid.

Süntaks:

CREATE PROCEDURE protseduur
    @parameeter andmetüüp
AS
BEGIN
    -- SQL laused
END
Käivitamine:

EXEC protseduur 'väärtus'
Näide 1 – Protseduur, mis lisab reа tabelisse
-- Proceduur, mis täidab tabeli
Create Procedure lisa
    @First_Name varchar(15)
AS
Begin
    Insert into Brands
    values (@First_Name);
    select * from Brands;
end

-- Kutse (käivitamine):
Exec lisa 'test'
Selgitus:

Protseduur nimega lisa võtab ühe parameetri @First_Name (kuni 15 tähemärki)
Lisab väärtuse tabelisse Brands
Kuvab kogu tabeli sisu pärast lisamist
Kutse: EXEC lisa 'test' — lisab nime 'test'
Näide 2 – Protseduur, mis kustutab rea ID järgi
-- Proceduur, mis kustutab tabelist id järgi
Create procedure kustuta
    @id int
AS
Begin
    SELECT * from Brands;
    Delete from Brands where brand_id = @id;
    Select * from Brands
End

-- Kutse:
EXEC kustuta 3
Selgitus:

Protseduur kustuta võtab täisarvu parameetri @id
Kuvab tabeli enne kustutamist
Kustutab rea, kus brand_id = @id
Kuvab tabeli pärast kustutamist
Kutse: EXEC kustuta 3 — kustutab rea, mille ID on 3
Näide 3 – Protseduur, mis otsib nime esitähe järgi
Create Procedure otsing
    @taht char(1)
AS
Begin
    Select Brand_Name from Brands
    where Brand_Name like @taht + '%';
End

-- Kutse:
Exec otsing 'N'
Selgitus:

Protseduur otsing võtab ühe tähe parameetri @taht
Otsib kõik Brand_Name väärtused, mis algavad selle tähega
LIKE @taht + '%' — % tähendab "ükskõik mis järgneb"
Kutse: EXEC otsing 'N' — kuvab kõik brändid, mille nimi algab N-tähega


kood:

CREATE DATABASE sandraloomad

CREATE TABLE loomapood( --teeb/loob tabeli.
    Id int PRIMARY KEY IDENTITY(1,1),
    Loomanimi varchar(50) NOT NULL,
    paritolu varchar(50),
    kogus int DEFAULT 1,
    Hind money
);

SELECT * FROM loomapood; --esimene tulemus, peaks tuhi olema (alguses ainult, kui midagi muud pole kaivitatud)

INSERT INTO loomapood(Loomanimi, paritolu, Hind) --kogu kupatus koos
VALUES ('sisalik', 'Austraalia', 5.90);

INSERT INTO loomapood (Loomanimi, paritolu, kogus, Hind)
VALUES ('kass', 'Eesti', 3, 25.50);

INSERT INTO loomapood (Loomanimi, paritolu, kogus, Hind)
VALUES ('koer', 'Saksamaa', 2, 120.00);

INSERT INTO loomapood (Loomanimi, paritolu, kogus, Hind)
VALUES ('hamster', 'Hiina', 10, 8.90);

INSERT INTO loomapood (Loomanimi, paritolu, kogus, Hind)
VALUES ('papagoi', 'Brasiilia', 1, 75.00);

INSERT INTO loomapood (Loomanimi, paritolu, kogus, Hind)
VALUES ('kilpkonn', 'Aafrika', 4, 60.00);

SELECT * FROM loomapood; --2 tulemus, koos andmetega

CREATE PROCEDURE lisaloom    -- kuni end, 43
    @nimetus varchar(50),
    @paritolu varchar(50),
    @kogus int,
    @hind money
AS
BEGIN
    INSERT INTO loomapood(Loomanimi, paritolu, kogus, Hind)
    VALUES (@nimetus, @paritolu, @kogus, @hind);

END;

EXEC lisaloom 'kass','Eesti',1,3.90; --see ja alumine lahevad koos, 3 tulemus
SELECT * FROM loomapood; 

EXEC lisaloom 'elevant', 'Louna-aafrika',6,78.99;   --uus variant
SELECT * FROM loomapood;

CREATE PROCEDURE minmaxHindLoom  --end'ini koos
    @minHind MONEY OUTPUT,
    @maxHind MONEY OUTPUT
AS
BEGIN
    SELECT 
        @minHind = MIN(Hind),
        @maxHind = MAX(Hind)
    FROM loomapood;
END;

DECLARE @min MONEY, @max MONEY;  -- rida 59- 64 koos, tulemus

EXEC minmaxHindLoom @min OUTPUT, @max OUTPUT;

PRINT @min;
PRINT @max; 

CREATE PROCEDURE muudaLoom --create kuni end, error voib olla kui juba jooksutatud
    @id int,
    @hind money
AS
BEGIN
    UPDATE loomapood
    SET Hind = @hind
    WHERE Id = @id;
END;

EXEC muudaLoom 1, 50; --76 ja 77 koos, tulemus
SELECT * FROM loomapood;

EXEC muudaLoom 3, 20; --variant 2
SELECT * FROM loomapood;

CREATE PROCEDURE kustutaLoom  --jalle create kuni end
    @id int
AS
BEGIN
    DELETE FROM loomapood WHERE Id = @id; --kustutab looma id, muutmiseks muuta looma id nr
END;

EXEC kustutaLoom 4;  --86 ja 87, tulemus
SELECT * FROM loomapood;

EXEC kustutaLoom 7; --variant 2
SELECT * FROM loomapood;


CREATE PROCEDURE otsiLoom   --koos select kuni end
    @nimi varchar(50)
AS
BEGIN
    SELECT * FROM loomapood
    WHERE Loomanimi LIKE @nimi + '%';
END;

EXEC otsiLoom 'k';  -- uksi, tulemus

EXEC otsiLoom 's'; --var 2

CREATE PROCEDURE loomaHinnaklass --kuni end
AS
BEGIN
    SELECT Loomanimi, Hind,
    CASE 
        WHEN Hind > 50 THEN 'Kallis loom'  --vajadusel muuta nt 50 suuremaks viói vaiksemaks
        ELSE 'Odav loom'
    END AS hinnaklass
    FROM loomapood;
END;

ALTER TABLE loomapood ADD varv varchar(50); --uksi, uuesti jookstes peab panema uue nime varv asemele, salvestab muidu ara

SELECT * FROM loomapood;  --uksi, viimane

