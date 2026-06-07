Andmebaasi võtmed (Keys)
Select laused | Protseduurid | vaade | Kasutaja | keys | küsimused | Triggerid

Andmebaasi võtmed on vahendid, millega tuvastatakse ridu tabelites, luuakse seoseid tabelite vahel ja tagatakse andmete unikaalsus ning terviklus.

1. Primary Key (Primaarvõti)
Definitsioon: Primary Key on veerg (või veergude kombinatsioon), mis tuvastab iga rea tabelis unikaalselt. Tabelil saab olla ainult üks primaarvõti.

Milleks kasutatakse: Iga rea üheseks identifitseerimiseks. Näiteks õpilase ID, arve number, tellimuse kood.

Mille poolest erineb:

Ei tohi olla NULL
Peab olema unikaalne
Iga tabelil ainult üks
Näide:

CREATE TABLE Õpilased (
    õpilane_id   INT PRIMARY KEY,
    eesnimi      VARCHAR(50),
    perenimi     VARCHAR(50)
);

INSERT INTO Õpilased VALUES (1, 'Mari', 'Mägi');
INSERT INTO Õpilased VALUES (2, 'Jaan', 'Kask');
<img width="425" height="635" alt="image" src="https://github.com/user-attachments/assets/d9c9f821-6097-48ab-9ac9-559f258f3d93" />

2. Foreign Key (Võõrvõti)
Definitsioon: Foreign Key on veerg, mis viitab teise tabeli primaarvõtmele. See loob seose kahe tabeli vahel.

Milleks kasutatakse: Tabelite vaheliste seoste loomiseks ja referentsiaalse tervikluse tagamiseks — ei saa lisada andmeid, mis ei eksisteeri viidatavas tabelis.

Mille poolest erineb:

Viitab alati teise tabeli PK-le
Võib olla NULL (kui seos on valikuline)
Ühes tabelis võib olla mitu Foreign Key-d
Näide:

CREATE TABLE Klassid (
    klass_id    INT PRIMARY KEY,
    klassinimi  VARCHAR(10)
);

CREATE TABLE Õpilased (
    õpilane_id  INT PRIMARY KEY,
    eesnimi     VARCHAR(50),
    klass_id    INT FOREIGN KEY REFERENCES Klassid(klass_id)
);

INSERT INTO Klassid VALUES (1, '10A');
INSERT INTO Õpilased VALUES (1, 'Mari', 1);
<img width="744" height="342" alt="image" src="https://github.com/user-attachments/assets/22df8cba-a7d3-403a-8545-49c7790e8764" />
<img width="220" height="125" alt="image" src="https://github.com/user-attachments/assets/37669b93-2578-43b9-83bb-568769e21556" />

3. Unique Key (Unikaalne võti)
Definitsioon: Unique Key tagab, et kõik veerus olevad väärtused on unikaalsed, kuid erinevalt Primary Key-st lubab ühe NULL-väärtuse.

Milleks kasutatakse: Kui tuleb tagada unikaalsus, aga tegemist ei ole peamise identifikaatoriga. Nt e-posti aadress, isikukood, telefoninumber.

Mille poolest erineb:

Lubab NULL-i (PK ei luba)
Tabelil võib olla mitu Unique Key-d
Ei ole tabeli peamine identifikaator
Näide:

CREATE TABLE Kasutajad (
    kasutaja_id  INT PRIMARY KEY,
    eesnimi      VARCHAR(50),
    email        VARCHAR(100) UNIQUE
);

INSERT INTO Kasutajad VALUES (1, 'Mari', 'mari@kool.ee');
INSERT INTO Kasutajad VALUES (2, 'Jaan', 'jaan@kool.ee');
-- Järgmine rida annab vea, sest email on juba olemas:
-- INSERT INTO Kasutajad VALUES (3, 'Tiiu', 'mari@kool.ee');
<img width="499" height="342" alt="image" src="https://github.com/user-attachments/assets/7697ec83-e7c6-4b43-830d-17868f347eb2" />

4. Simple Key (Lihtne võti)
Definitsioon: Simple Key koosneb ainult ühest veerust, mis tuvastab rea unikaalselt.

Milleks kasutatakse: Kõige levinum võtme tüüp — üks veerg (nt ID) identifitseerib rea.

Mille poolest erineb:

Ainult üks veerg (erinevalt Composite ja Compound Key-st)
Lihtsaim ja selgeim võtme vorm
Näide:

CREATE TABLE Tooted (
    toode_id    INT PRIMARY KEY,   -- Simple Key: ainult üks veerg
    toode_nimi  VARCHAR(100),
    hind        DECIMAL(10,2)
);

INSERT INTO Tooted VALUES (1, 'Pliiats', 0.99);
INSERT INTO Tooted VALUES (2, 'Vihik', 1.49);
<img width="421" height="344" alt="image" src="https://github.com/user-attachments/assets/f6a6d78f-84a2-4a42-a9ea-c734363152fe" />

5. Composite Key (Liitvõti)
Definitsioon: Composite Key on primaarvõti, mis koosneb kahest või enamast veerust. Ükski veerg eraldi ei tuvasta rida unikaalselt — ainult koos.

Milleks kasutatakse: Seosetabelites (junction tables), kus ühe tabeli rida seob kahte teist tabelit. Nt õpilane saab olla mitmes kursuses ja kursusel on mitu õpilast.

Mille poolest erineb:

Mitu veergu moodustavad koos võtme
Kasutatakse M:N seoste lahendamiseks
Ükski üksikveerg pole üksi primaarvõti
Näide:

CREATE TABLE Kursused (
    kursus_id   INT PRIMARY KEY,
    kursuse_nimi VARCHAR(100)
);

CREATE TABLE Õpilane_Kursus (
    õpilane_id  INT,
    kursus_id   INT,
    PRIMARY KEY (õpilane_id, kursus_id),   -- Composite Key
    FOREIGN KEY (õpilane_id) REFERENCES Õpilased(õpilane_id),
    FOREIGN KEY (kursus_id)  REFERENCES Kursused(kursus_id)
);

INSERT INTO Õpilane_Kursus VALUES (1, 101);
INSERT INTO Õpilane_Kursus VALUES (1, 102);
INSERT INTO Õpilane_Kursus VALUES (2, 101);
<img width="501" height="508" alt="image" src="https://github.com/user-attachments/assets/b5f05af6-c52e-49c8-976d-be8e05f74a6f" />
<img width="476" height="536" alt="image" src="https://github.com/user-attachments/assets/f7cf686f-99e6-430d-8e48-d90837edb07e" />

6. Compound Key (Liitidentifikaator)
Definitsioon: Compound Key on sarnane Composite Key-ga — koosneb mitmest veerust — kuid erinevalt Composite Key-st sisaldab vähemalt ühte Foreign Key veergu.

Milleks kasutatakse: Tabelites, kus võti on moodustatud seosveergudest (FK-dest).

Mille poolest erineb:

Sisaldab Foreign Key veerge (Composite Key ei pruugi)
Rõhutab, et võtme osad on seosed teiste tabelitega
Näide:

CREATE TABLE Tellimuse_Toode (
    tellimus_id  INT,   -- FK - Tellimused
    toode_id     INT,   -- FK - Tooted
    kogus        INT,
    PRIMARY KEY (tellimus_id, toode_id),          -- Compound Key
    FOREIGN KEY (tellimus_id) REFERENCES Tellimused(tellimus_id),
    FOREIGN KEY (toode_id)    REFERENCES Tooted(toode_id)
);
<img width="526" height="461" alt="image" src="https://github.com/user-attachments/assets/10e2b6e0-492e-4d30-bbeb-8436d2a65051" />
<img width="534" height="502" alt="image" src="https://github.com/user-attachments/assets/a125cbbb-ce25-4060-8880-91519cf0c1e7" />

7. Superkey (Supervõti)
Definitsioon: Superkey on ükskõik milline veergude kombinatsioon, mis tuvastab rea unikaalselt. Superkey võib sisaldada "üleliigseid" veerge.

Milleks kasutatakse: Teoreetiline mõiste andmebaasi disainis — aitab mõista, millised veergude kombinatsioonid suudavad ridu unikaalselt identifitseerida.

Mille poolest erineb:

Võib sisaldada mittevajalikke veerge
Candidate Key on Superkey minimaalne versioon (ilma üleliigsete veergudeta)
Kõik Candidate Key-d on Superkey-d, aga mitte vastupidi
Näide:

CREATE TABLE Töötajad (
    töötaja_id   INT PRIMARY KEY,
    eesnimi      VARCHAR(50),
    perenimi     VARCHAR(50),
    isikukood    CHAR(11) UNIQUE
);

-- Kõik järgmised on Superkey-d (tuvastavad rea unikaalselt):
-- (töötaja_id)
-- (isikukood)
-- (töötaja_id, eesnimi)         - üleliigne, aga toimib
-- (töötaja_id, eesnimi, perenimi) - üleliigne, aga toimib
-- 7. SUPERKEY / 8. CANDIDATE KEY / 9. ALTERNATE KEY

<img width="696" height="339" alt="image" src="https://github.com/user-attachments/assets/4d166b0b-91c4-46db-91ed-76f1bfeb6c6a" />

8. Candidate Key (Kandidaatvõti)
Definitsioon: Candidate Key on minimaalne Superkey — veerg või veergude kombinatsioon, mis tuvastab rea unikaalselt ilma üleliigsete veergudeta. Tabelil võib olla mitu Candidate Key-d.

Milleks kasutatakse: Andmebaasi disainis — ühest Candidate Key-st saab Primary Key, ülejäänud saavad Alternate Key-deks.

Mille poolest erineb:

Minimaalne (ei sisalda üleliigseid veerge)
Võib olla mitu tabelis
Üks neist valitakse PK-ks
Näide:

CREATE TABLE Õpetajad (
    õpetaja_id   INT UNIQUE NOT NULL,   -- Candidate Key 1
    isikukood    CHAR(11) UNIQUE NOT NULL, -- Candidate Key 2
    tööemail     VARCHAR(100) UNIQUE NOT NULL, -- Candidate Key 3
    eesnimi      VARCHAR(50),
    perenimi     VARCHAR(50)
);

-- Kõik kolm veergu on Candidate Key-d:
-- igaüks tuvastab rea unikaalselt ja on minimaalne
-- Tavaliselt valitakse õpetaja_id - Primary Key
9. Alternate Key (Alternatiivvõti)
Definitsioon: Alternate Key on Candidate Key, mida ei valitud Primary Key-ks. See on "varuidentifikaator".

Milleks kasutatakse: Alternatiivne viis rea tuvastamiseks. Nt isikukood on AK siis, kui primaarvõtmeks on valitud ID-number.

Mille poolest erineb:

On Candidate Key, aga mitte PK
Rakendatakse tavaliselt UNIQUE constraintina
Tabelil võib olla mitu AK-d
Näide:

CREATE TABLE Õpilased (
    õpilane_id   INT PRIMARY KEY,          -- Primary Key (valitud Candidate Key)
    isikukood    CHAR(11) UNIQUE NOT NULL, -- Alternate Key
    email        VARCHAR(100) UNIQUE,      -- Alternate Key
    eesnimi      VARCHAR(50),
    perenimi     VARCHAR(50)
);

INSERT INTO Õpilased VALUES (1, '50501010001', 'mari@kool.ee', 'Mari', 'Mägi');
Allikad:

Microsoft Learn – Primary and Foreign Key Constraints (SQL Server) https://learn.microsoft.com/en-us/sql/relational-databases/tables/primary-and-foreign-key-constraints?view=sql-server-ver17
Microsoft Learn – Create Unique Constraints (SQL Server) https://learn.microsoft.com/en-us/sql/relational-databases/tables/create-unique-constraints?view=sql-server-ver17
W3Schools – SQL PRIMARY KEY Constraint https://www.w3schools.com/sql/sql_primarykey.asp
W3Schools – SQL FOREIGN KEY Constraint https://www.w3schools.com/sql/sql_foreignkey.asp
GeeksForGeeks – Composite Key in SQL https://www.geeksforgeeks.org/sql/composite-key-in-sql/
database.guide – How to Create a Composite Primary Key in SQL Server https://database.guide/how-to-create-a-composite-primary-key-in-sql-server-t-sql-example/
GeeksForGeeks – Keys in Relational Model https://www.geeksforgeeks.org/dbms/types-of-keys-in-relational-model-candidate-super-primary-alternate-and-foreign/
GeeksForGeeks – Candidate Key in DBMS https://www.geeksforgeeks.org/dbms/candidate-key-in-dbms/
GeeksForGeeks – SQL Alternate Key https://www.geeksforgeeks.org/sql/sql-alternate-key/
