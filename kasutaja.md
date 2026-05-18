1. Windows Authentication

Selle puhul kasutatakse samu kasutajaandmeid, millega logitakse sisse Windows operatsioonisüsteemi.

    Kasutajanimi ja parool on seotud Windowsiga
    Turvalisem lahendus
    Paroole haldab Windows
    Kasutaja ei pea eraldi SQL Serveri parooli teadma

2. SQL Server Authentication

Selle puhul luuakse kasutaja otse SQL Serverisse.

    Kasutaja ei ole seotud Windowsiga
    Määratakse eraldi kasutajanimi ja parool
    Sobib veebirakenduste jaoks

Näide kasutajast: DirectorNimi
Parool: director
Kasutaja loomine SQL Serveris

1. Serveritaseme kasutaja loomine (Login)
Sammud

Ava:

Security → Logins

Tee paremklikk ja vali:

New Login...


>>>>>pilt<img width="699" height="653" alt="{EE3D8BDF-1161-499D-A3EE-D0B82924809C}" src="https://github.com/user-attachments/assets/894cc52c-d2a8-43a9-9e32-a9c3cfd2da5e" />


Harjutamiseks võib eemaldada linnukese:  User must change password at next login

Server Roles

Menüüst Server Roles saab määrata serveri üldised õigused.

Tavaliselt piisab rollist: public


>>>>>pilt<img width="684" height="615" alt="{01C66169-3332-49C5-BD49-324A0D614E54}" src="https://github.com/user-attachments/assets/0239b8dc-8282-4bf5-ac02-c80ae5a9599e" />


2. Andmebaasi kasutaja loomine (User)

Ava:

Database → Security → Users

Tee paremklikk:  New User...

Seosta kasutaja loginiga

>>>>>pilt 

Membership ja õigused

Menüüst Membership saab määrata kasutaja rollid.

    db_datareader → võib lugeda SELECT
    db_datawriter → võib kirjutada INSERT, UPDATE, DELETE


>>>>>pilt <img width="909" height="815" alt="{10C705F2-751D-4CD2-8D2C-B5338BD463EF}" src="https://github.com/user-attachments/assets/803a8e07-8a58-427c-b1a7-92a1f59e63f0" />


SQL Server Authentication Mode muutmine
Kui ilmub viga: Error 18456, siis on tavaliselt lubatud ainult Windows Authentication.
Lahendus

    Server → Properties
    Security
    Vali: SQL Server and Windows Authentication mode

GRANT käsud õiguste jagamiseks

GRANT käsuga antakse kasutajale õigused.
Käsk 	Tähendus
SELECT 	Lugemine
INSERT 	Lisamine
UPDATE 	Muutmine
DELETE 	Kustutamine


>>>>>pilt <img width="485" height="507" alt="{A9DD01B9-891D-4763-A83A-5E538BDCAD7A}" src="https://github.com/user-attachments/assets/8fd14409-15ab-4268-91d2-2e70422a65d3" />


<img width="490" height="653" alt="{B201D6EA-AEA0-4082-BEA7-EAB00739F990}" src="https://github.com/user-attachments/assets/c5d4706e-a76d-47f1-bac7-98ac8cf477f3" />



<img width="552" height="575" alt="{EF917187-9ECD-4FB3-B895-2D3E6A5DED96}" src="https://github.com/user-attachments/assets/3abb5870-2a80-4295-97b1-36ff2fa85d74" />


<img width="685" height="953" alt="{E739B353-FB3A-431F-B04C-C74B1D3BDB03}" src="https://github.com/user-attachments/assets/2ab34d40-a808-4cd4-9c59-ba94adf3c1fc" />


<img width="593" height="767" alt="{37DDEDCB-EA11-47C3-B0AC-D37D114EF84D}" src="https://github.com/user-attachments/assets/b5ab6518-2bd1-4dc7-b49f-a1e26bec7a5d" />


Ülesanne 1:

Luua andmebaas: MovieBase

Luua tabelid: 

    movies (id, moviesNimi, moviesYear, movieDir и movieCost).

    guest (id, name)

Lisada vähemalt 7 kirjet.

Luua kasutaja Produtsent parooliga director, kellel on järgmised õigused:

    Õigus vaadata ja uuendada tabeli movies välju movieDir ja movieCost + lisada üks enda valitud privileeg.
    Õigus vaadata ja lisada kirjeid tabelisse guest.
    Keela andmete kustutamine tabelis.

Vihje! UPDATE õigused parem lubada SQL käsuga

GRANT UPDATE (movieCost, movieDir)
ON movies
TO Produtsent;
    
