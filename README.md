# Patika.dev-SQL
Patika.dev SQL patikası Ödev 1,Ödev 2 ve Ödev 3 queryleri   

* [Ödev 1](#ödev-1)

* [Ödev 2](#ödev-2)

* [Ödev 3](#ödev-3)

* [Ödev 4](#ödev-4)

* [Ödev 5](#ödev-5)

* [Ödev 6](#ödev-6)

* [Ödev 7](#ödev-7)

* [Ödev 8](#ödev-8)

* [Ödev 9](#ödev-9)

* [Ödev 10](#ödev-10)

* [Ödev 11](#ödev-11)

## Ödev 1

#### `film` tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
```sql
SELECT title, description 
FROM film
```
#### `film` tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük `VE` 75 ten küçük olma koşullarıyla sıralayınız.
```sql
SELECT *
FROM film
WHERE length > 60 AND length < 75
```
#### `film` tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 `VE` replacement_cost 12.99 `VEYA` 28.99 olma koşullarıyla sıralayınız
```sql
SELECT * 
FROM film
WHERE rental_rate = 0.99 AND replacement_cost = 12.99 OR replacement_cost = 28.99
```
#### `customer` tablosunda bulunan `first_name` sütunundaki değeri 'Mary' olan müşterinin `last_name` sütunundaki değeri nedir? 
```sql
SELECT first_name,last_name
FROM customer
WHERE first_name = 'Mary'
```
#### `film` tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```sql
SELECT *
FROM film
WHERE NOT length > 50 AND NOT (rental_rate = 2.99 OR rental_rate = 4.99)
```

## Ödev 2

#### `film` tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
```sql
SELECT * 
FROM film
WHERE replacement_cost BETWEEN 12.99 AND 16.99 and replacement_cost != 16.99
```

#### `actor` tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
```sql
SELECT first_name,last_name
FROM actor
WHERE first_name IN ('Penelope','Nick','Ed')
```
#### `film` tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. (IN operatörünü kullanınız.)
```sql
SELECT *
FROM film
WHERE rental_rate IN (0.99,2.99,4.99) AND replacement_cost IN (12.99,15.99,28.99)
```

## Ödev 3

#### `country` tablosunda bulunan `country` sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
```sql
SELECT *
FROM country
WHERE country LIKE 'A%a'
```

#### `country` tablosunda bulunan `country` sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
```sql
SELECT *
FROM country
WHERE country LIKE '_____%n'
```

#### `film` tablosunda bulunan `title` sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
```sql
SELECT title
FROM film
WHERE title ILIKE '%t%t%t%t%'
```

#### `film` tablosunda bulunan tüm sütunlardaki verilerden `title` 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
```sql
SELECT *
FROM film
WHERE title LIKE 'C%' AND length > 90 AND rental_rate = 2.99
```

## Ödev 4

#### film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
```sql
SELECT DISTINCT replacement_cost
FROM film
```

#### film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

```sql
SELECT count(DISTINCT replacement_cost)
FROM film
```

#### film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
```sql
SELECT COUNT(title)
FROM film
WHERE title LIKE 'T%'
AND rating  = 'G'
```

#### country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```sql
SELECT COUNT(country)
FROM country
WHERE country LIKE '_____'
```

#### city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

```sql
SELECT COUNT(city)
FROM city
WHERE city LIKE 'R%r'
```

## Ödev 5

#### film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
```sql
SELECT *
FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 5
```

#### film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
```sql
SELECT *
FROM film
WHERE title LIKE '%n'
ORDER BY length ASC
LIMIT 5
```

#### customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
```sql
SELECT title,length
FROM film
WHERE title LIKE '%n'
ORDER BY length DESC
LIMIT 4
```

## Ödev 6

#### film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

```sql
SELECT ROUND(AVG(rental_rate),2) 
FROM film;
```

#### film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
```sql
SELECT COUNT(*)
FROM film
WHERE title LIKE 'C%';
```

#### film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
```sql
SELECT MAX(length)
FROM film
WHERE rental_rate = 0.99
```

#### film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
```sql
SELECT COUNT(DISTINCT replacement_cost)
FROM film
WHERE length > 150;
```

## Ödev 7

#### film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
```sql
SELECT rating
FROM film
GROUP BY rating
```

#### film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
```sql
SELECT replacement_cost, COUNT(*)
FROM film
GROUP BY replacement_cost
HAVING COUNT(*) > 50;
```

#### customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
```sql
SELECT store_id, COUNT(*)
FROM customer
GROUP BY store_id;
```

#### city tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
```sql
SELECT country_id,COUNT(*)
FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;
```

## Ödev 8

#### test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
```sql
CREATE TABLE employee (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50),
    birthday DATE,
	email VARCHAR(50),
);
```

#### Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.
```sql
insert into MOCK_DATA (id, first_name, birthday, email) values (1, 'Ursuline', '2006-01-31', 'umozzetti0@tiny.cc');
insert into MOCK_DATA (id, first_name, birthday, email) values (2, 'Wendi', '2016-08-21', 'wcaldecourt1@blogspot.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (3, 'Linea', '2020-11-17', 'lfarnhill2@pen.io');
insert into MOCK_DATA (id, first_name, birthday, email) values (4, 'Sonnie', '2011-04-08', 'sangus3@etsy.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (5, 'Natalee', '2013-03-17', 'nlydall4@un.org');
insert into MOCK_DATA (id, first_name, birthday, email) values (6, 'Royal', '2004-12-13', 'rdecullip5@seattletimes.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (7, 'Cordy', '2016-08-03', 'cdanson6@photobucket.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (8, 'Isa', '2014-08-02', 'imcneilly7@i2i.jp');
insert into MOCK_DATA (id, first_name, birthday, email) values (9, 'Lotte', '2018-12-24', 'lkleinplatz8@mysql.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (10, 'Yancy', '2004-08-20', 'ymolineux9@yelp.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (11, 'Simmonds', '2004-11-12', 'spechea@liveinternet.ru');
insert into MOCK_DATA (id, first_name, birthday, email) values (12, 'Kinnie', '2006-02-03', 'kfarndonb@paypal.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (13, 'Sonny', '2020-06-18', 'shavardc@mozilla.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (14, 'Sophey', '2004-09-11', 'segiloffd@quantcast.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (15, 'Irita', '2014-09-16', 'iblockeye@buzzfeed.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (16, 'Debbi', '2017-02-14', 'dboswardf@de.vu');
insert into MOCK_DATA (id, first_name, birthday, email) values (17, 'Jodi', '2013-12-26', 'jtilteg@huffingtonpost.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (18, 'Hillard', '2017-04-27', 'hbraksperh@fotki.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (19, 'Tanny', '2007-04-14', 'tbaldoccii@chicagotribune.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (20, 'Franzen', '2012-05-29', 'fdeavesj@digg.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (21, 'Brice', '2019-02-27', 'bmellerk@canalblog.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (22, 'Bondon', '2009-10-27', 'bolekhovl@mapquest.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (23, 'Eleanore', '2016-12-10', 'edenyaginm@aol.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (24, 'Stephanie', '2015-09-10', 'sdeathn@xinhuanet.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (25, 'Doloritas', '2021-02-09', 'dstanfieldo@va.gov');
insert into MOCK_DATA (id, first_name, birthday, email) values (26, 'Vince', '2020-01-27', 'vbrainep@boston.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (27, 'Laughton', '2011-07-10', 'lfeasbyq@sciencedaily.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (28, 'Cyb', '2017-05-03', 'crosenbaumr@ask.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (29, 'Rabi', '2012-02-01', 'rleybornes@hubpages.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (30, 'Ambur', '2005-09-01', 'aklauert@wp.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (31, 'Floyd', '2021-03-22', 'feykelhofu@illinois.edu');
insert into MOCK_DATA (id, first_name, birthday, email) values (32, 'Ursa', '2012-02-12', 'uubsdalev@jiathis.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (33, 'Vivyanne', '2019-12-14', 'vclackw@fc2.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (34, 'Caesar', '2005-06-13', 'cwurzx@ifeng.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (35, 'Angelle', '2009-06-18', 'aboshersy@mayoclinic.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (36, 'Teriann', '2020-12-12', 'tnealandz@amazon.co.uk');
insert into MOCK_DATA (id, first_name, birthday, email) values (37, 'Ardyce', '2021-05-12', 'aradden10@dot.gov');
insert into MOCK_DATA (id, first_name, birthday, email) values (38, 'Robina', '2017-07-07', 'rmccrie11@vkontakte.ru');
insert into MOCK_DATA (id, first_name, birthday, email) values (39, 'Beniamino', '2011-08-11', 'bodonohue12@hud.gov');
insert into MOCK_DATA (id, first_name, birthday, email) values (40, 'Millard', '2011-04-20', 'mkinnett13@rediff.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (41, 'Kylie', '2016-04-27', 'kcreak14@slashdot.org');
insert into MOCK_DATA (id, first_name, birthday, email) values (42, 'Birch', '2006-03-25', 'bdickman15@sciencedirect.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (43, 'Hope', '2015-08-15', 'hshacklady16@imageshack.us');
insert into MOCK_DATA (id, first_name, birthday, email) values (44, 'Judas', '2011-01-25', 'jmcilhone17@zimbio.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (45, 'Umeko', '2013-03-22', 'utroucher18@amazonaws.com');
insert into MOCK_DATA (id, first_name, birthday, email) values (46, 'Chickie', '2015-03-14', 'chighton19@epa.gov');
insert into MOCK_DATA (id, first_name, birthday, email) values (47, 'Selene', '2019-09-21', 'svines1a@upenn.edu');
insert into MOCK_DATA (id, first_name, birthday, email) values (48, 'Aurelia', '2018-04-17', 'alingwood1b@pagesperso-orange.fr');
insert into MOCK_DATA (id, first_name, birthday, email) values (49, 'Rozina', '2007-08-02', 'rposselow1c@uiuc.edu');
insert into MOCK_DATA (id, first_name, birthday, email) values (50, 'Tully', '2003-01-30', 'tbramsom1d@list-manage.com');
```

#### Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.
```sql
UPDATE employee
SET name = 'Update_t'
WHERE name LIKE 'T%';

UPDATE employee
SET email = 'Update_email_last'
WHERE name LIKE '%com';

UPDATE employee
SET name = '30th Index'
WHERE id = 30;

UPDATE employee
SET email = 'Update_email'
WHERE email LIKE 'a%';

UPDATE employee
SET name = 'Update_id'
WHERE id > 30;
```

#### Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.
```sql
DELETE FROM employee
WHERE name LIKE 'T%';

DELETE FROM employee
WHERE name LIKE '%com';

DELETE FROM employee
WHERE id = 30;

DELETE FROM employee
WHERE email LIKE 'a%';

DELETE FROM employee
WHERE id > 30;
```

## Ödev 9
#### city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
SELECT city, country
FROM city
INNER JOIN country
ON city.country_id = country.country_id
```

#### customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazın
```sql
SELECT payment_id,first_name,last_name
FROM customer
INNER JOIN payment
ON customer.customer_id = payment.customer_id;
```

#### customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.
```sql
SELECT rental_id,first_name,last_name
FROM customer
INNER JOIN rental
ON customer.customer_id = rental.customer_id;
```

## Ödev 10
#### city tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.
```sql
SELECT city, country
FROM city
LEFT JOIN country
ON city.country_id = country.country_id
```

#### customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.
```sql
SELECT payment_id,first_name,last_name
FROM customer
RIGHT JOIN payment
ON customer.customer_id = payment.customer_id;
```

#### customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz
FULL JOIN sorgusunu yazınız.
```sql
SELECT rental_id,first_name,last_name
FROM customer
FULL JOIN rental
ON customer.customer_id = rental.customer_id;
```

## Ödev 11

#### actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.
```sql
(SELECT first_name
FROM actor
)
UNION
(SELECT first_name
FROM customer)
```

#### actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.
```sql
(SELECT first_name
FROM actor
)
INTERSECT
(SELECT first_name
FROM customer)
```

#### actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.
```sql
(SELECT first_name
FROM actor
)
EXCEPT
(SELECT first_name
FROM customer)
```

#### İlk 3 sorguyu tekrar eden veriler için de yapalım.
```sql
(SELECT first_name
FROM actor
)
UNION ALL
(SELECT first_name
FROM customer);

(SELECT first_name
FROM actor
)
INTERSECT
(SELECT first_name
FROM customer);

(SELECT first_name
FROM actor
)
EXCEPT ALL
(SELECT first_name
FROM customer);

```
