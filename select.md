## Select laused SQL

[Select laused](select.md) | [Protseduurid](Protseduur.md) | [vaade](vaade.md) | [Kasutaja](kasutaja.md) | [keys](keys.md) | [küsimused](kysimused.md) |


<img width="1362" height="823" alt="image" src="https://github.com/user-attachments/assets/fa7340db-1505-4345-98a3-7da0612ee29a" />



```sql
create database selectSandraM
use selectSandraM
create table auto(
autonumber char(6) primary key,
mark varchar(30),
mudell varchar(50),
v_aasta int,
varv varchar(50),
hind money)

select * from auto

--mockaroo.com 


insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('144YvQ', 'Ford', 'Probe', 1994, 'Blue', '€931,13');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('927iCv', 'Volvo', 'S40', 2007, 'Fuscia', '€1250,52');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('203Ual', 'Volvo', 'C70', 2007, 'Indigo', '€2601,43');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('497y2s', 'Land Rover', 'Range Rover', 2001, 'Purple', '€4543,15');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('927OGh', 'Dodge', 'Charger', 1968, 'Teal', '€8078,54');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('015fyO', 'Kia', 'Amanti', 2008, 'Maroon', '€5829,52');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('771GDR', 'Pontiac', 'Grand Prix', 1971, 'Pink', '€9728,77');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('380ES0', 'Chevrolet', 'Vega', 1971, 'Aquamarine', '€445,23');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('428r7v', 'Pontiac', 'Sunfire', 1997, 'Aquamarine', '€2031,40');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('957BNo', 'Mazda', 'B-Series', 2009, 'Aquamarine', '€8541,61');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('093PI4', 'Spyker', 'C8 Spyder', 2004, 'Crimson', '€8797,22');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('211Bul', 'Lincoln', 'Town Car', 1998, 'Orange', '€3310,78');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('6858qH', 'Mitsubishi', 'Pajero', 1994, 'Puce', '€285,12');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('499278', 'Mazda', 'Mazdaspeed6', 2006, 'Orange', '€7503,39');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('1482gX', 'Mitsubishi', 'Galant', 2004, 'Orange', '€1751,37');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('323KaZ', 'Chevrolet', 'S10', 1994, 'Puce', '€456,30');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('867cxD', 'Dodge', 'D350', 1992, 'Indigo', '€5339,13');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('688ROn', 'Ford', 'Mustang', 2009, 'Violet', '€6076,56');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('794cAF', 'Ram', 'Dakota', 2011, 'Purple', '€1476,74');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('319saJ', 'Subaru', 'Forester', 2007, 'Blue', '€804,64');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('053WR2', 'Isuzu', 'Rodeo', 1999, 'Violet', '€6405,89');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('743MMl', 'Buick', 'Lucerne', 2009, 'Mauv', '€1294,26');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('773Tqh', 'Ford', 'Thunderbird', 1995, 'Goldenrod', '€9985,13');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('402K6L', 'Lincoln', 'MKX', 2011, 'Aquamarine', '€8854,12');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('4042JI', 'Mitsubishi', 'Precis', 1990, 'Mauv', '€1281,81');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('373oFG', 'Chevrolet', 'Corvette', 1968, 'Blue', '€5954,14');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('890Vyd', 'Dodge', 'Intrepid', 1995, 'Blue', '€6418,78');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('741CcI', 'Acura', 'NSX', 1998, 'Aquamarine', '€7130,91');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('967zRp', 'Dodge', 'Avenger', 1996, 'Violet', '€3087,13');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('607exO', 'Honda', 'Element', 2008, 'Puce', '€1575,04');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('130Qsk', 'BMW', '7 Series', 1993, 'Blue', '€4301,57');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('554Am9', 'Chevrolet', 'Camaro', 1969, 'Red', '€2532,45');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('723cRb', 'Bentley', 'Azure', 2010, 'Violet', '€1414,96');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('056XwS', 'Lexus', 'GS', 2004, 'Teal', '€5273,63');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('61033v', 'Mercury', 'Grand Marquis', 1992, 'Crimson', '€2121,82');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('9379O7', 'Lexus', 'LS', 2006, 'Yellow', '€9797,40');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('529Tdm', 'Ford', 'Escort', 2004, 'Turquoise', '€2777,64');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('978CoE', 'Chevrolet', '2500', 1992, 'Green', '€5544,01');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('583lxW', 'Volkswagen', 'GTI', 1991, 'Khaki', '€2542,21');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('126CvX', 'Chevrolet', 'Malibu', 2005, 'Teal', '€9366,95');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('463Sg1', 'Pontiac', 'Montana SV6', 2005, 'Mauv', '€8401,89');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('212UyU', 'Saab', '900', 1993, 'Khaki', '€9871,63');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('65325U', 'GMC', 'Vandura 1500', 1992, 'Mauv', '€4646,10');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('463hka', 'Chevrolet', 'Camaro', 1996, 'Turquoise', '€5161,14');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('221RdX', 'Suzuki', 'Equator', 2011, 'Aquamarine', '€1710,88');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('939ciu', 'Plymouth', 'Voyager', 2000, 'Teal', '€4969,99');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('142F9X', 'Volvo', 'C70', 2003, 'Teal', '€2555,99');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('587Y7C', 'Chevrolet', 'Silverado 3500', 2011, 'Teal', '€6446,82');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('988X6H', 'Acura', 'RL', 2007, 'Yellow', '€4940,35');
insert into MOCK_DATA (autonumber, mark, mudel, v_aasta, varv, hind) values ('288LUi', 'Land Rover', 'Freelander', 2010, 'Red', '€2624,65');


```

```sql

--Näita kõik
Select * from auto
-- Näita ainult mark, mudel ja hind
select mark, mudell, hind from auto
--tingimused
-- sorteerimine -Order by -kasvavalt, DESC - kahanevalt
Select mark, mudell, hind
from auto
order by hind DESC;

```
<img width="706" height="497" alt="image" src="https://github.com/user-attachments/assets/3c9d47ad-2a78-431d-85f9-4a8c493483f7" />



```sql

-- mark algab C tähega
select mark from auto
where mark like 'C%'

```
<img width="278" height="294" alt="image" src="https://github.com/user-attachments/assets/c36766c8-de83-4e8a-886f-c5bbc5b84283" />




```sql


--hind on vahemikus 500-800
select hind, autonumber, mark 
from auto
Where hind > 5000 and hind <8000 

--teine variant
select hind, autonumber, mark 
from auto
Where hind between 5000 and 10000

-- kombineeritud tingimused (AND, OR, NOT)
select hind, autonumber, mark 
from auto
Where mark lIKe 'Volkswagen' or hind <= 100000

--vaate loomine - VIEW
create view VolkswagenAutod
as
select hind, autonumber, mark 
from auto
Where mark lIKe 'Volkswagen' 

--view kasutamine
Select * from VolkswagenAutod

```

```sql
--Agregaatfunktsioond - SUM, MAX, MIN, AVG, COUNT-kogus

--Leia mitu autot on tabelis
Select count(*) as autodeArv from auto

--Leia keskmine autohind 
Select AVG(hind) as keskmineHind from auto

--Leia keskmine autohind iga margi kohta
Select mark, AVG(hind) as keskmineHind 
from auto
GROUP by mark
```
