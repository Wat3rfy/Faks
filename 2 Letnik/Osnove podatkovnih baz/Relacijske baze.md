

### SQL

Imamo operacije vrste **DML** oz. **Data manipulation langauge**, in **DDL** oz. **Data definition language**.

Pod DML spadajo **select, insert, update, delete**, namanjeni neposrednemu delu s podatki znotraj tabel. medtem ko pod DDL spadajo create, alter, set transaction, ki služijo definiranju in upravljanju strukture baze in njenih objektov.

**SQL**je enostaven, nepostopkoven, večnamenski, in je uveljaven kot standardni jezik za delo z relacijskimi bazami.
***
**DML skupine**

- SELECT, 
- UPDATE, 
- INSERT, 
- DELETE
***
**SELECT**

```sql
SELECT [DISTINCT|ALL]
{*|[columnExpression[AS newName]][,...]}
FROM table-name [alias][,...]
[WHERE condition]
[GROUP BY columnList] 
[HAVING condition]
[ORDER BY columnList]
```

`SELECT` določa stolpce ki naj se pojavijo v izhodni relaciji.
`FROM` določa tabele za poizvedbo
`WHERE` filtrira vrstice
`GROUP BY` Združuje vrstice po vrednostih izbranih stolpcev
`HAVING` Filtrira skupine glede na določene pogoje
`ORDER BY` Določa vrstni red vrstic na izhodu

Vrstnega reda sklopov ni možno spreminjati, obvezna pa sta le `SELECT` in `FROM` sklopa.

SQL izrazi so **neobčutljivi** na velikost črk.

Rezervirane besede SQL ne smemo uporabljati za definicije.

```sql
select * from table-name;
//Izbere vse stolpce iz tabele.

select col1, col2 from table-name;
//Izbere stolpca col1 in col2 iz tabele.

select distinct atr-name from table-name;
//Izpiše vse distinktne vrednosti ki nastopajo v stolpcu.

select first_name, last_name, birth_date, hire_date, DATEDIFF(hire_date, birth_date)/365 as 'Starost ob zaposlitvi' from employees;
//ali
select first_name, last_name, YEAR(hire_date)-YEAR(birth_date) as 'Starost ob zaposlitvi' from employees;
//Izpiše starost ob zaposlitvi
```

Primeri funkcij v mySQL SUPB


| Name | Description | Example SQL Usage | Example Result (Based on hypothetical input) |
| :--- | :--- | :--- | :--- |
| **ADDDATE()** | Add time values (intervals) to a date value | `SELECT ADDDATE('2024-06-01', INTERVAL 5 DAY);` | `2024-06-06` |
| **ADDTIME()** | Add time | `SELECT ADDTIME('10:00:00', '01:30:00');` | `11:30:00` |
| **CONVERT\_TZ()** | Convert from one timezone to another | `SELECT CONVERT_TZ('2024-06-01 10:00:00', 'UTC', 'EST');` | `2024-06-01 06:00:00` |
| **CURDATE()** | Return the current date | `SELECT CURDATE();` | `2024-10-27` (Current Date) |
| **CURRENT\_DATE(),** | Synonyms for CURDATE() | `SELECT CURRENT_DATE;` | `2024-10-27` (Current Date) |
| **CURRENT\_TIME(),** | Synonyms for CURTIME() | `SELECT CURRENT_TIME();` | `14:35:50` (Current Time) |
| **CURRENT\_TIMESTAMP()** | Synonyms for NOW() | `SELECT CURRENT_TIMESTAMP;` | `2024-10-27 14:35:50` (Current Datetime) |
| **CURTIME()** | Return the current time | `SELECT CURTIME();` | `14:35:50` (Current Time) |
| **DATE\_ADD()** | Add time values (intervals) to a date value | `SELECT DATE_ADD('2024-01-01', INTERVAL 3 MONTH);` | `2024-04-01` |
| **DATE\_FORMAT()** | Format date as specified | `SELECT DATE_FORMAT(NOW(), '%W, %M %D, %Y');` | `Sunday, October 27th, 2024` |
| **DATE\_SUB()** | Subtract a time value (interval) from a date | `SELECT DATE_SUB('2024-06-30', INTERVAL 1 WEEK);` | `2024-06-23` |
| **DATE()** | Extract the date part of a date or datetime expression | `SELECT DATE('2024-10-27 15:45:00');` | `2024-10-27` |
| **DATEDIFF()** | Subtract two dates (returns difference in days) | `SELECT DATEDIFF('2024-07-01', '2024-06-01');` | `30` |
| **DAY()** | Synonym for DAYOFMONTH() | `SELECT DAY('2024-11-15');` | `15` |
| **DAYNAME()** | Return the name of the weekday | `SELECT DAYNAME('2024-11-15');` | `Friday` |


**Iskalni kriteriji**

Izpiši vse zaposlene, ki so moškega spola in so rojeni pred 1953. 

```sql
select * from employees 
where YEAR(birth_date)<1953 and gender = 'M';
```

Uporaba logičnih operatorjev kot so and, or, not, =, <, <=, != pri `where`.

Posebnejši: 
- between (preverja vrednosti v intervalu), 
- like(preverja po nekeme vzorcu npr. `A%`), 
- in (preverja vrednosti v podanem seznamu), 
- is null, 
- is not null, 
- **all**, 
- **any**, 
- **exists**

kjer so all, any in exists uporabljeni pri poizvedbi na drugi tabeli.

**All** - gledamo ali je cena večja od vseh v drugi tabeli.

```sql
SELECT ime_izdelka, cena FROM Izdelki 
WHERE cena > ALL ( 
SELECT cena FROM Izdelki 
WHERE oddelek = 'Oblačila' );
```

**Any** - gledamo ali je cena večja od vsaj ene v drugi tabeli

**Exsists** - gledamo če je 

```sql
SELECT id_izdelka, ime_izdelka FROM Izdelki I WHERE EXISTS ( SELECT 1 FROM Narocila N WHERE N.id_izdelka = I.id_izdelka );
```

*Select 1 je sintaksa kjer pri njeni uporabi preverjamo le obstoj vrstice in ne zaravljamo časa z branjem in prenašanjem dejanskih podatkov ampak preverjam le obstoj vrstice; 1 je le standardna konstanta, lahko bi pisalo tudi selet NULL, select  'A'...*

**Leta** so shranjena po `YYYY-MM-DD`, **čas** je srhanjen kot `HH:MM:SS`, **datetime** pa kot `YYYY-MM-DD HH:MM:SS`.

Obstaja tudi `CAST`: 
```sql 
SELECT CAST('2025-10-27' AS DATE);
```

Primer iskanja po članstvu v množici

```sql
select * from titles 
where title in ('Staff', 'Senior Staff');
```


Primer iskanja z vzorcem

```sql
select * from employees 
where last_name like 'B%' and birth_date like '__6_____01';
//Imena ki se začnenjo na B in rojeni prvega v mesecu v šestedesetih
```

Iskanje z NULL

```sql
select * from employees 
where hire_date is null;
```

**Sortiranje vrstic**

```sql
select emp_no, last_name, birth_date from employees 
order by last_name, birth_date desc;
```

**Agregiranje podatkov**

ISO standard definira pet agregarnih operacij
- `COUNT` - število vrednosti
- `SUM` - seštevek vrednosti
- `AVG` - povprečje vrednosti
- `MIN` - minimalna vrednost
- `MAX` - največja vrednost

Vse delujejo samo na enem stolpcu.
`COUNT, MIN, MAX` se uporabljajo z numeričnimi in nenumeričnimi vrednostmi,
`SUM, AVG` zahtevata na numerične vrednosti

Vse operacije razen `COUNT(*)` najprej odstranijo vrstice `NULL`  po katerem agregirajo.

`COUNT(*)` prešteje vse vrstice ne glede na `NULL` vrednosti ali duplikate.

Če se želimo znebiti duplikatov uporabimo `DISTINCT` pred imenom stolpca.

Agregatne operacije lahko uporabljamo le v `SELECT` ali `HAVING` sklopu.

Če `SELECT` sklop vsebuje agregatno operacij potem mora obstajati tudi `GROUP BY` sklop, sicer ni mogoče dodeliti agregirane vrednosti.

```sql
select emp_no, avg(salaray)
from salaries
group by emp_no;
```

Primer uporabe distinct s count.

```sql
select count(distinct title) from titles;
```

Lahko izpišeš več agregatnih operacij

```sql
select avg(salary), max(salary), min(salary) from salaries
```

**Združevanje podatkov**

`GROUP BY` združuje podatke v skupine kjer se ponovi isti podatek.

```sql
select emp_no, avg(salary) from salaries
group by emp_no;
```

Pogleda vse vrednosti v stolpcu `emp_no` in agregiramo po vrsticah le če sta `emp_no` enaki.

**Pravila**

1\. Če v select stavku dodamo stolpec ki ni del agragatne funkcije potem moramo na koncu grupirati po njemu.

2\. Vedno se najprej izvede WHERE združevanje pa na preostalih vrsticah.

3\. Vrstice ki so `NULL` se grupirajo v svojo grupo oz. so obravnavane kot vrednost po kateri se grupira.

**Omejitve skupin**

`HAVING` sklop postavlja pogoje katerim morajo zadoščati skupine v rezultatu. *Stolpci v `HAVING` sklopu morajo biti tudi v select sklopu ali agregatih.*

Vgnezdeni `SELECT` stavki se lahko uporabljajo v `WHERE` ali `HAVING` sklopih drugega `SELECT` stavka. *subselect*

*Izpiši imena in priimke zaposlenih, ki so delali na vsaj treh delovnih mestih.*

```sql
select first_name, last_name from employees 
where emp_no in ( 
select emp_no from titles 
group by emp_no 
having count(*) > 2 );
```

Primer uporabe aliasov za gnezdene poizvedbe

```sql
select P.product_serial, P.model_name, P.customer_id from Products P where P.product_serial in ( select S.product_serial from Service_Logs S where P.warranty_end_date >= S.service_date );
```

Primer uporabe select vgnezdenja pri where in z logičnim operatorjem

```sql
select first_name, last_name from employees where emp_no in ( select emp_no from salaries where (select max(salary) from salaries) = salary);
```

Primer uporabe kot operanda

```sql
select emp_no,  
avg(salary) - (select avg(salary) from salaries)  
from salaries  
group by emp_no;
```

**Pravilav SQL ki se jih v mySQL ne upoštevajo**
- select vgnezdeega stavka lahko zajema le en stolpec
- ko je vgnezden select stavek operand v primerjavi se mora nahajati na desni strani enačbe
- vgenzdeni select stavek nemore biti operand v izrazu


**Uporaba ANY, ALL**

**`ANY/SOME`** bo izpolnjen če bo izpolnjen pogoj za vsaj eno vrednost poizvedbe.
`ALL` bo izpolnjen če velja za vse vrednosti poizvedbe.

Če je rezultat poizvedbe prazen bo `ALL` vrnil `true`, `ANY/SOME` pa `false`.

*Primer uporabe any*

**Uporaba `EXISTS`**

`EXSITS` lahko uporabljamo le v vgnezdenih poizvedbah in vrača true če obstaja vrstica v tabeli vgnezdene poizvedbe, false pa če vgnezdena poizvedba vrača prazno množico.

Lahko uporabljamo tudi `NOT EXISTS`

**Pozvedbe po več tabelah**

Po več tabelah lahko izvajamo poizvedbe z vgnezdenimi `SELECT` stavki, kjer so stolpc v rezultatu lahko le iz ene tabele.

V poizvedbah ki vračaji stolpce različnih tabel moramo uporabljati stik.

Za ločevanje istoimenskih stolpcev uporabljamo sinonime

```sql
select E.emp_no, E.first_name, E.last_name
from employees E, dept_manager DM, departments D
where
E.emp_no = DM.emp_no AND
DM.dept_no = D.dept_no;
```

Alternativni načini stika med več tabelami: 

```sql
FROM employees E JOIN titles T ON E.emp_no = T.emp_no
FROM employees JOIN titles USING emp_noFROM employees NATURAL JOIN titles
```
 

Zgornji zapisi nadomestijo sklopa `FROM` in `WHERE` 
V prvem primeru rezultat vsebuje dva identična stolpca

**Operacije nad množicami**

Rezultate dveh ali več poizvedb lahko združujemo z ukazi:
- UNION 
- INTERSECITON 
- DIFFERENCE

Da lahko izvajamo te operacije morata tabeli `A` in `B` biti skladni - domene atributov morata biti enake.

```sql
op [ALL] [CORRESPONDING [BY {column1 [,...]}]] 
```

Če uporabmo `CORRESPONDING BY` se operacije izvede samo nad poimenovanimi stolpci.

Če uporabimo samo `CORRESPONDING` brez `BY` člena, se operacija izvede na skupnimi stolpci.

Če uporabimo `ALL` lahko rezultat vključuje tudi dvojnike.

Primer unije

```sql
select EM.first_name, EM.last_name, 'Moški' from (
	select * from employees 
	where gender = 'M' 
	order by hire_date desc limit 3
) EM 
union select EF.first_name, EF.last_name, 'Ženske' from (
	select * from employees 
	where gender = 'F' 
	order by hire_date desc limit 3
) EF;
```

**Insert stavek**

```sql
INSERT INTO ime-tabele [ (columnList) ] VALUES (dataValueList)
```

Seznam `columnList` ni obvezen.
Pri vnosu moramo vpisati najmanj vse obvezne vrednosti (tiste ki so not null) razen za stolpce s privzeto vrednostjo
Seznam `dataValueList` mora ustrezati seznamu `columnList`

```sql
insert into departments (dept_no, dept_name) values ('d010', 'Education');
```

Vnos več vrstic iz ene ali več drugih tabel

```sql
INSERT INTO TableName [ (columnList) ] 
SELECT ...
```

**UPDATE stavek**

```sql
UPDATE TableName SET columnName1 = dataValue1 [, columnName2 = dataValue2...] [WHERE searchCondition] 
```

`tableName` se lahko nanaša na ime osnovne tabele ali ime pogleda.

Sklop `SET` določa nazive enega ali več stolpcev ter nove vrednosti teh stolpcev

`WHERE` sklop neobvezen

```sql
update salaries set salary = salary * 1.1 where to_date = '9999-01-01'
```

**DELETE stavek**

```sql
DELETE FROM tableName
WHERE searchCondition
```

`tableName` se lahko nanaša na ime osnovne tabele ali ime pogleda.

`WHERE` sklop ni obvezen. Če ga spustimo, zbrišemo vse vrstice v tabeli, tabela pa ostane.

```sql
delete from salaries where emp_no not in ( select emp_no from salaries where to_date = '9999-01-01' );
```

***

**Stavki skupine DDL**

DDL (data definition language) zajema SQL stavke za manipulacijo s strukturo podatkovne baze.

Poznamo podatkovne tipe v sql

| Data type | Declarations |
|---|---|
| boolean | BOOLEAN |
| character | CHAR, VARCHAR |
| bit | BIT, BIT VARYING |
| exact numeric | NUMERIC, DECIMAL, INTEGER, SMALLINT |
| approximate numeric | FLOAT, REAL, DOUBLE PRECISION |
| datetime | DATE, TIME, TIMESTAMP |
| interval | INTERVAL |
| large objects | CHARACTER LARGE OBJECT, BINARY LARGE OBJECT |

V mysql pa

| Category | Data Types |
|---|---|
| **Numeric** (Integer Types) | TINYINT, SMALLINT, MEDIUMINT, INT, BIGINT |
| **Numeric** (Fixed-Point Types) | DECIMAL, NUMERIC |
| **Numeric** (Floating-Point Types) | FLOAT, DOUBLE |
| **Numeric** (Bit-Value Type) | BIT |
| **String** | CHAR, VARCHAR, BINARY, VARBINARY, BLOB, TEXT, ENUM, SET |
| **Date & Time** | DATE, TIME, DATETIME, TIMESTAMP, YEAR |


**Zagotavljanje kakovosti podatkov**

SQL standard ponuja več vrst omejitev kot so
- obveznost podatkov (not null)
- omejitve domene (value has to be)
- pravila za celovitost podatkov (identifikacijski stolpec oz. ključ)
	- celovitost entitet (primarni ključ)
	- celovitost povezav (veljavne povezave za tuji ključ)
- števnost
- splošne omejitve

Omejitve so lahko definirane v `CREATE` in `ALTER TABLE`.

Obveznost podatkov
```sql
emp_no numeric(5) NOT NULL
```

Omejitve domene
```sql
gender CHAR NOT NULL CHECK (gender in ('M', 'F'))
```

Lahko ustvarimo domeno

```sql
CREATE DOMAIN DomainName [AS] dataType
[DEFAULT defaultOption]
[CHECK (searchCondition)]
```

Primer
```sql
CREATE DOMAIN Tgender AS CHAR
CHECK (VALUE IN ('M', 'Ž'));
```

Uopraba domene v definiciji stolpca
```sql
gender Tgender NOT NULL
```

**Zagotovaljanje kakovosti podatkov**

`searchCondition` lahko vsebuje iskalno tabelo:

```sql
CRETE DOMAIN TempID AS numeric(5)
CHECK (VALUE IN (SELECT emp_no FROM employees));
```

Domeno lahko ukinemo z uporabo stavka `DROP DOMAIN`:

```sql
DROP DOMAIN DomainName
[RESTRICT | CASCADE]
```

`RESTRICT | CASCADE` povesta kako ravnati če je domena trenutno v uporabi.

ISO standard podpira kreiranje primarnih ključev in tujih ključev v okviru `CREATE`in `ALTER TABLE` stavkov.

```sql
PRIMARY KEY(dept_no, emp_no)
FOREIGN KEY(emp_no) REFERENCES employees
```

Določimo lahko enolične stolpce ali kombinacije stolpcev

```sql
UNIQUE(last_name)
UNIQUE(last_name, first_name)
```

**Celovitost povezav**

če ima FK neko vrednost potem se mora ta vrednost nahajati v primarnem ključu povezane tabele

Vsak `INSERT/UPDATE` stavek ki skuša kreirati FK vrednost v tabeli, brez da bi ta vrednost obstajala ko PK v povezani tabeli, je zavrnjen.

Ob zavrnitvi so možne naslednje akcije
- `CASCADE`
- `SET NULL`
- `SET DEFAULT`
- `NO ACTION`

Določimo z uporabo

`ON UPDATE, ON DELETE, ON UPDATE SET NULL`

npr.

```sql
FOREIGN KEY (emp_no) REFERENCES employees ON DELETE CASCADE
```


**IEF - splošne omejitve**

SPlošne omejitve določimo z `CHECK/UNIQUE` opcijami v `CREATE` in `ALTER TABLE` stavkih.

```sql
CREATE ASSERTION AssertionName
CHECK (searchCondition)
```

npr.

```sql
CREATE ASSERTION PrevecSprememb 
CHECK not exists ( 
	select count(*) from salaries 
	group by emp_id, YEAR(date_from) 
	having count(*) > 3 
);
```


**Ustvarjanje podatkovnih objektov**

SQL DDL omogoča kreranje in birsanje podatkovnih objektov kot so: **shema, domena, tabela, pogled, indeks**.

```sql
CREATE SCHEMA DROP SCHEMA 
CREATE/ALTER DOMAIN DROP DOMAIN 
CREATE/ALTER TABLE DROP TABLE 
CREATE/ALTER VIEW DROP VIEW 
CREATE INDEX DROP INDEX
```

Relacije in drugi podatkovni objekti obstajajo v nekem okolju.

Vsako okolje vsebuje enega ali več katalogov, vsak **katalog** pa **množico shem**.
**Shema** je pomenovana **kolekcija povezanih podatkovnih objektov**.
Obejkti v shemi so lahko **tabele, pogledi, domene, trditve, dodelitve, pretvorbe** in **znakovni nizi**.

Različne implementacije sql imajo razlike v poimenovanju.

(SQL)
Strežnik $\rightarrow$ Instanca $\rightarrow$ Katalog $\rightarrow$ Shema $\rightarrow$ Tabela

(mySQL)
Strežnik $\rightarrow$ Instanca $\rightarrow$ Katalog $\rightarrow$ Tabela

**Ustvarjanje sheme**

```sql
CREATE SCHEMA [Name | AUTHORIZATION CreatorId ] 

DROP SCHEMA Name [RESTRICT | CASCADE]
```

`RESTRICT` (privzeto): shema mora biti prazna, sicer brisanje ni možno.

`CASCADE`: kaskadno se brišejo vsi objekti, povezani s shemo. Če katerokoli brisanje ne uspe, se zavrne celotna operacija.

**Ustvarjanje tabele**

```sql
CREATE TABLE TableName 
({colName dataType [NOT NULL] [UNIQUE]
 [DEFAULT defaultOption] 
 [CHECK searchCondition] [,...]} 
 [PRIMARY KEY (listOfColumns),] 
 {[UNIQUE (listOfColumns),] […,]} 
 {[FOREIGN KEY (listOfFKColumns)
	  REFERENCES ParentTableName [(listOfCKColumns)], 
	  [ON UPDATE referentialAction] 
	  [ON DELETE referentialAction ]] [,…]} {[CHECK (searchCondition)]
```

Primer

```sql
CREATE TABLE dept_manager ( dept_no CHAR(4) NOT NULL, emp_no INT(11) NOT NULL, from_date DATE NOT NULL, to_date DATE NOT NULL, PRIMARY KEY (emp_no, dept_no), CONSTRAINT dept_manager_ibfk_1 FOREIGN KEY (emp_no) REFERENCES employees(emp_no) ON DELETE CASCADE, CONSTRAINT dept_manager_ibfk_2 FOREIGN KEY (dept_no) REFERENCES departments (dept_no) ON DELETE RESTRICT)
```

**ALTER TABLE**

S tem stavkom lahko
- dodajamo ali ukinjamo stolpce v tabeli
- dodajamo ali ukinjamo omejitve v tabeli
- za stolpce v tabeli določamo ali ukinjamo privzete vrednosti
- spreminjamo podatkovne tipe stolpcev v tabeli

```sql
ALTER TABLE dept_manager ALTER from_date DROP DEFAULT;
```

Spremeni tabelo `salaries` tako, da ukineš omejitev `prevecSPrememb`. Tabeli `employees` dodaj stolpec `retired` s privzeto vrednost `n`.

```sql
ALTER TABLE salaries DROP CONSTRAINT PrevecSprememb; 

ALTER TABLE employees ADD retired CHAR(1) NOT NULL DEFAULT 'N';
```

Primeri

```sql
ALTER TABLE employees ADD nickname AFTER first_name; 
ALTER TABLE employees CHANGE first_name fn;
ALTER TABLE employees MODIFY birth_date date NULL; 
ALTER TABLE employees ALTER gender SET DEFAULT ’M’; 
ALTER TABLE employees DROP gender; DESCRIBE employees;
```

**DROP TABLE**

Z `DROP TABLE` lahko ukinemo tabelo, hkrati pa izbrišemo vse zapise v tabeli.

```sql
DROP TABLE tableName [RESTRICT | CASCADE]
```

```sql
DROP TABLE employees RESTRICT;
```

**Indeksi**

Omogočajo urejanje tabel po različnihstolpcih. So ključnega pomena za hitro poizvedovanje.

Sintaksa

```sql
CREATE [UNIQUE] INDEX index_name 
ON table_name 
	(column1 [ASC|DESC], 
	column2 [ASC|DESC], 
	...);
```

V mysql

```sql
CREATE [UNIQUE|FULLTEXT|SPATIAL] INDEX index_name [USING {BTREE|HASH}] ON tbl_name (index_col_name,...) [index_option][algorithm_option|lock_option]
```

Primer

```sql
CREATE INDEX idx_emp_fullname_gender ON employees (first_name ASC, last_name DESC, gender); 


SHOW INDEX FROM employees;
```


**Pogledi**

Predstavljajo navidezne tabele. Vsakokrat ko dostopamo do pogleda se v ozadju izvede SELECT stavek.

```sql
CREATE VIEW view_name [(column_list)] 
AS select_statement 
[WITH [CASCADED | LOCAL] CHECK OPTION]
```

Primer

```sql
CREATE VIEW Managers AS SELECT e.emp_no, e.first_name, e.last_name, d.dept_name, dm.from_date FROM employees e JOIN dept_manager dm ON e.emp_no = dm.emp_no JOIN departments d ON d.dept_no = dm.dept_no WHERE dm.to_date = '9999-01-01';
```


**Transakcije**

SQL definira **transakcijski model** z ukazoma `COMMIT` in `ROLLBACK`.

**Transakcija** je logična enota ki dela z enim ali več ukazi. Je **atomarna**.

Spremembe znotraj transakcije praviloma drugim transakcijam skrite, dokler transakcija ni končana.

Lahko se zaključi **eksplicitno** (`COMMIT/ROLLBACK`) ali **implicitno** (skupaj s programom  v katerem je klicana).

Nova transakcija se začne z novim SQL stavkom, ki transakcijo inicira.

SQL transakcij ne moremo gnezditi.

Transakcijo nastavimo z `SET TRANSACTION`

```sql
SET TRANSACTION 
[READ ONLY | READ WRITE] | 
[ISOLATION LEVEL READ UNCOMMITTED | 
READ COMMITTED|REPEATABLE READ |SERIALIZABLE ]
```

`READ ONLY` - pove, da transakcija vključuje samo operacije, ki iz baze berejo *SUPB bo dovolil insert, update, delete samo na začasnimi tabelami*

`ISOLATION LEVEL` pove stopnjo interakcije ki so SUPB dovlo med to in drugimi transakcijami.
- `READ UNCOMITTED`
- `READ COMMITED`
- `REPEATABLE READ`
- `SERIALIZABLE`

Varen je samo način `SERIALIZABLE`



**Dirty read** ki se lahko zgodi pri izolaciji `READ UNCOMMITED`

**Non-repeatable read** se lahko zgodi pri izolacijskih ravneh **Read Commited, Read Uncommited**

**Phantom read** se lahko zgodi pri vseh izolacijskih ravenh razen pri **Serializable**.

![[Pasted image 20251023164355.png]]

**Delo s transakcijami v mySQL**

```sql
SET TRANSACTION [GLOBAL|SESSION] [READ ONLY | READ WRITE] | [ISOLATION LEVEL READ UNCOMMITTED | READ COMMITTED|REPEATABLE READ |SERIALIZABLE ]

mysql> START TRANSACTION
mysql> SET TRANSACTION ISOLATION LEVEL SERIALIZABLE
```

Inicializacija transakcije...
