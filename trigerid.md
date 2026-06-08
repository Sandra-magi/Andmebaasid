## Triger - trigger - päästik

Select laused | Protseduurid | vaade | Kasutaja | keys | küsimused | Triggerid
Triger - andmebaasi objekt, mis käivitub automaatselt, kui toimub steatud sündmus (nt INSERT, UPDATE , DELETE).

Trigerite loomine - automatseerub protsessid SQL Serveris

Tabelid mis tuleb luua enne trigerit!

create database trigerLogitpe24

use trigerLogitpe24
Create table linnad(
linnId int primary key identity (1, 1),
linnanimi varchar(30) unique,
maakond varchar(50),
rahvarv int)
select * from linnad

insert into linnad(linnanimi, maakond, rahvarv)
Values('Tallinn', 'Harjumaa', 600000);

--tabeli logi - tabel, mis täidab triger, kui kasutaja täidab tabeli linnad!
Create table logi(
id int primary key identity(1, 1),
kasutaja varchar(50),
aeg datetime,
andmed TEXT)

--1. Triger lisatud andmete jälgimiseks tabelis linnad,
--jälgib andmete sisestamine tabelisse ja teeb vastava kirje logi-tabelise

Create trigger linnaLisamine
On linnad -- tabel, mis triger jälgib
for insert
as
insert into logi(kasutaja, aeg, andmed)
select
SYSTEM_USER, --siselogitud user
GETDATE(), 
concat('lisatud: ', inserted.linnanimi, ', ', inserted.maakond, ', ', inserted.rahvarv)
from inserted;

--kontrollimiseks tuleb lisada linna tabelisse linnad
insert into linnad(linnanimi, maakond, rahvarv)
Values('Viljandi', 'Viljandimaa', 50000);

select * from linnad
select * from logi

<img width="648" height="578" alt="{7B48FC0D-7D60-4E24-B0F0-0B0A501D932B}" src="https://github.com/user-attachments/assets/0b90c63c-ec7a-4e18-8085-05386d1adfc5" />


--2. Delete triger - jälgib kustutamibe tabelis linnad 
--ja teeb vastava kirje logi tabelisse

Create trigger linnaKustutamine
On linnad -- tabel, mis triger jälgib
for delete
as
insert into logi(kasutaja, aeg, andmed)
select
SYSTEM_USER, --siselogitud user
GETDATE(), 
concat('kustutatud: ', deleted.linnanimi, ', ', deleted.maakond, ', ', deleted.rahvarv)
from deleted;

--kontroll
Delete from linnad where linnId=2

<img width="585" height="565" alt="{129306A6-45EA-4956-A499-0CCCD8D13DD8}" src="https://github.com/user-attachments/assets/384148aa-1228-40c2-96bd-9c7ba153ca1a" />


--3.Update Trigger - jälgib uuendused/muutused tabelis linnad
--ja teeb vastava kirje tabelis logi

Create trigger linnaUuendamine
On linnad -- tabel, mis triger jälgib
for update
as
insert into logi(kasutaja, aeg, andmed)
select
SYSTEM_USER, --siselogitud user
GETDATE(), 
concat('vana andmed : ',
deleted.linnanimi, ', ', deleted.maakond, ', ', deleted.rahvarv,
' ||| uued andmed: ',
inserted.linnanimi, ', ', inserted.maakond, ', ', inserted.rahvarv)
from deleted INNER JOIN inserted
on deleted.linnId=inserted.linnId;

--kontroll
Update linnad set linnanimi='Tallinn22', rahvarv=700000
where linnId=1


--triger sisse/välja lülitamine
Disable Trigger linnaLisamine on linnad
Disable Trigger linnaKustutamine on linnad
Enable trigger linnaUuendamine ON linnad
Enable trigger linnaKustutamine on linnad
<img width="326" height="195" alt="{4D685E7B-3CFE-4BBF-BEFE-E827665C7FB3}" src="https://github.com/user-attachments/assets/ce742578-81c6-48fd-9347-b1070fe06073" />


--Ühine triger mis jälgib kas lisamine või kustutamine tabelisse linnad
Create trigger linnaLisamineKustutamine
On linnad -- tabel, mis triger jälgib
for insert, Delete
as
begin
set nocount on; 
	insert into logi(kasutaja, aeg, andmed)
	select
	SYSTEM_USER, --siselogitud user
	GETDATE(), 
	concat('lisatud: ', inserted.linnanimi, ', ', 
	inserted.maakond, ', ', inserted.rahvarv)
	from inserted

	UNION all 

	select
	SYSTEM_USER, --siselogitud user
	GETDATE(), 
	concat('kustutatud: ', deleted.linnanimi, ', ', 
	deleted.maakond, ', ', deleted.rahvarv)
	from deleted;
end;

--kontroll
Delete from linnad where linnId=3

insert into linnad(linnanimi, maakond, rahvarv)
Values('Viljandi', 'Viljandimaa', 50000);

select * from linnad
select * from logi

<img width="762" height="661" alt="{715862F6-DE49-4EF3-8F9F-C2C19D90C46B}" src="https://github.com/user-attachments/assets/52fd7c53-bf61-4576-821a-2b8186320b44" />
