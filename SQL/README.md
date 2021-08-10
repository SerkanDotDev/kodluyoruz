
## ÖDEV 1

1. film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.

```sql
SELECT title , description FROM film
```

2. film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.

```SQL
SELECT * FROM film 
 WHERE length BETWEEN 61 AND 74
```

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.

```sql
SELECT * FROM film
 WHERE rental_rate = 0.99 
 AND
 (replacement_cost = 12.99 OR replacement_cost = 28.99) 
```

4. customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?

```sql
SELECT last_name FROM customer
 WHERE first_name='Mary'  
```

5. film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.

```sql
SELECT * FROM film
 WHERE NOT length > 50 
 AND
 NOT (rental_rate = 2.99 OR rental_rate = 4.99 )

```
---

## ÖDEV 2

1. film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)

```sql
SELECT * FROM film 
 WHERE replacement_cost BETWEEN 12.99 AND 16.99;
```

2. actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)

```SQL
SELECT first_name, last_name FROM actor
 WHERE first_name 
 IN ('Penelope', 'Nick', 'Ed');       
```

3. film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız. ( IN operatörünü kullanınız.)

```sql
SELECT * FROM film
 WHERE rental_rate IN (0.99,2.99,4.99) 
 AND 
 replacement_cost IN (12.99,15.99,28.99);
```

---

## ÖDEV 3

1. country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.

```sql
SELECT country FROM country
 WHERE country 
 LIKE 'A%a';
```

2. country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.

```SQL
SELECT * FROM country 
 WHERE country LIKE '_____%n' ;
```

3. film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren film isimlerini sıralayınız.

```sql
SELECT title FROM film 
 WHERE title 
 ILIKE '%t%t%t%t%';
```

4. film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.

```sql
SELECT * FROM film
 WHERE title 
 LIKE 'C%'
 AND
 length > 90
 AND 
 rental_rate = 2.99;
```

---

## ÖDEV 4

1. film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.

```sql
SELECT DISTINCT replacement_cost FROM film;
```

2. film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?

```SQL
SELECT COUNT(DISTINCT replacement_cost) FROM film;
```

3. film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?

```sql
SELECT COUNT(*) FROM film
 WHERE title 
 LIKE 'T%'
 AND
 rating = 'G';
```

4. country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?

```sql
SELECT COUNT(*) FROM country
 WHERE length(country)=5;
```

5. city tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?

```sql
SELECT COUNT(*) FROM city 
 WHERE city ILIKE '%r';
```

---

## ÖDEV 5

1. Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.

```sql
SELECT * FROM film 
 WHERE title
 LIKE '%n'
 ORDER BY length DESC
 LIMIT 5;
```

2. Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.

```sql
SELECT * FROM film
 WHERE title
 LIKE '%n'
 ORDER BY length ASC
 OFFSET 5
 LIMIT 5;
```

3. Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.

```sql
SELECT * FROM customer
 WHERE store_id =1
 ORDER BY last_name DESC
 LIMIT 4;
```

---

## ÖDEV 6

1. Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?

```sql
SELECT ROUND(AVG(rental_rate),2) FROM film;
```

2. Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?

```sql
SELECT COUNT(*) FROM film
 WHERE title LIKE 'C%';
```

3. Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?

```sql
SELECT MAX(length) FROM film
 WHERE rental_rate = 0.99;
```

4. Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?

```sql
SELECT COUNT (DISTINCT replacement_cost) FROM film
 WHERE 
 length > 150;
```

---

## ÖDEV 7

1. Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.

```sql
SELECT * FROM film
 GROUP BY rating;
```

2. Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.

````sql
SELECT replacement_cost,COUNT(*) FROM film
 GROUP BY replacement_cost
 HAVING COUNT(*)>50;
````

3. Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?

````sql
SELECT store_id, COUNT(*) FROM customer 
 GROUP BY store_id;
````

4. City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.

````sql
SELECT country_id, COUNT(*) FROM city
 GROUP BY country_id
 ORDER BY COUNT(*) DESC
 LIMIT 1;
````
---


## ÖDEV 8

1. Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.

````sql
CREATE TABLE employee(
	id INTEGER NOT NULL,
	name VARCHAR(50) NOT NULL,
	birthday DATE NOT NULL,
	email VARCHAR(100) NOT NULL,
);
````

2. Oluşturduğumuz employee tablosuna 'Mockaroo' servisini kullanarak 50 adet veri ekleyelim.

````sql
insert into employee (id, name, birthday, email) values (1, 'Matteo', '2021-06-26', 'msturror0@dot.gov');
insert into employee (id, name, birthday, email) values (2, 'Andria', '2018-11-16', 'alanchester1@disqus.com');
insert into employee (id, name, birthday, email) values (3, 'Blanche', '2020-05-07', 'bmuzzullo2@discuz.net');
insert into employee (id, name, birthday, email) values (4, 'Konstantine', '2020-12-19', 'kmuress3@timesonline.co.uk');
insert into employee (id, name, birthday, email) values (5, 'Rodi', '2019-04-16', 'rhorrigan4@de.vu');
insert into employee (id, name, birthday, email) values (6, 'Niles', '2019-03-11', 'ngitting5@twitter.com');
insert into employee (id, name, birthday, email) values (7, 'Patton', '2019-02-25', 'pchattaway6@techcrunch.com');
insert into employee (id, name, birthday, email) values (8, 'Mord', '2017-08-11', 'mkenealy7@comcast.net');
insert into employee (id, name, birthday, email) values (9, 'Aaren', '2018-06-17', 'avalti8@wikia.com');
insert into employee (id, name, birthday, email) values (10, 'Chiarra', '2021-07-03', 'cashtonhurst9@adobe.com');
insert into employee (id, name, birthday, email) values (11, 'Giorgi', '2018-07-31', 'gtapsona@google.com.hk');
insert into employee (id, name, birthday, email) values (12, 'Staffard', '2020-11-11', 'sammerb@nih.gov');
insert into employee (id, name, birthday, email) values (13, 'Ketti', '2017-07-15', 'knickollc@go.com');
insert into employee (id, name, birthday, email) values (14, 'Hurley', '2017-06-28', 'hmilsapd@census.gov');
insert into employee (id, name, birthday, email) values (15, 'Kimmy', '2018-01-17', 'kjupee@yelp.com');
insert into employee (id, name, birthday, email) values (16, 'De', '2017-12-15', 'dwigzellf@canalblog.com');
insert into employee (id, name, birthday, email) values (17, 'Lincoln', '2017-08-25', 'lkenwayg@boston.com');
insert into employee (id, name, birthday, email) values (18, 'Lenee', '2017-09-12', 'lmiddleditchh@addthis.com');
insert into employee (id, name, birthday, email) values (19, 'Clarence', '2021-07-14', 'cstockporti@cdc.gov');
insert into employee (id, name, birthday, email) values (20, 'Jethro', '2020-02-07', 'jkesleyj@vimeo.com');
insert into employee (id, name, birthday, email) values (21, 'Chucho', '2019-03-18', 'celsmerek@washington.edu');
insert into employee (id, name, birthday, email) values (22, 'Skell', '2018-01-11', 'smackinl@abc.net.au');
insert into employee (id, name, birthday, email) values (23, 'Humfrey', '2021-06-21', 'halltimesm@yahoo.co.jp');
insert into employee (id, name, birthday, email) values (24, 'Valerie', '2017-07-18', 'vsharpleyn@csmonitor.com');
insert into employee (id, name, birthday, email) values (25, 'Tallia', '2021-01-05', 'tfilipchikovo@java.com');
insert into employee (id, name, birthday, email) values (26, 'Carmencita', '2021-01-13', 'cthewlisp@edublogs.org');
insert into employee (id, name, birthday, email) values (27, 'Ryann', '2020-04-01', 'rsmyeq@dot.gov');
insert into employee (id, name, birthday, email) values (28, 'Sapphire', '2018-01-21', 'sskippr@google.fr');
insert into employee (id, name, birthday, email) values (29, 'Giffie', '2019-11-21', 'gguyers@devhub.com');
insert into employee (id, name, birthday, email) values (30, 'Jaclin', '2019-06-27', 'jfromantt@cnbc.com');
insert into employee (id, name, birthday, email) values (31, 'Hillie', '2017-10-27', 'hcowlardu@hatena.ne.jp');
insert into employee (id, name, birthday, email) values (32, 'Vale', '2018-08-22', 'vronischv@blogtalkradio.com');
insert into employee (id, name, birthday, email) values (33, 'Arne', '2020-01-17', 'abacksalw@deliciousdays.com');
insert into employee (id, name, birthday, email) values (34, 'Aldin', '2018-03-25', 'agimenezx@behance.net');
insert into employee (id, name, birthday, email) values (35, 'Michele', '2018-12-19', 'mmuckloy@nymag.com');
insert into employee (id, name, birthday, email) values (36, 'Stephannie', '2020-11-04', 'srubinowitchz@nhs.uk');
insert into employee (id, name, birthday, email) values (37, 'Cathe', '2017-06-16', 'ckorejs10@sakura.ne.jp');
insert into employee (id, name, birthday, email) values (38, 'Conroy', '2018-10-31', 'cwindress11@seattletimes.com');
insert into employee (id, name, birthday, email) values (39, 'Inessa', '2017-08-05', 'iealam12@europa.eu');
insert into employee (id, name, birthday, email) values (40, 'Marne', '2019-08-28', 'meagan13@cornell.edu');
insert into employee (id, name, birthday, email) values (41, 'Damian', '2017-11-07', 'dpurvis14@globo.com');
insert into employee (id, name, birthday, email) values (42, 'Mia', '2020-03-28', 'mkanwell15@liveinternet.ru');
insert into employee (id, name, birthday, email) values (43, 'Ally', '2019-07-04', 'aishak16@state.tx.us');
insert into employee (id, name, birthday, email) values (44, 'Halley', '2019-06-27', 'hmargerrison17@virginia.edu');
insert into employee (id, name, birthday, email) values (45, 'Merry', '2018-09-16', 'mvonhagt18@privacy.gov.au');
insert into employee (id, name, birthday, email) values (46, 'Blondell', '2019-06-19', 'bmarczyk19@wikispaces.com');
insert into employee (id, name, birthday, email) values (47, 'Ettie', '2017-04-05', 'ecorssen1a@yellowpages.com');
insert into employee (id, name, birthday, email) values (48, 'Darlleen', '2018-03-24', 'daliman1b@vimeo.com');
insert into employee (id, name, birthday, email) values (49, 'Dalis', '2017-11-02', 'dholsey1c@fc2.com');
insert into employee (id, name, birthday, email) values (50, 'Estrellita', '2019-08-01', 'evongrollmann1d@answers.com');
````

3. Sütunların her birine göre diğer sütunları güncelleyecek 5 adet UPDATE işlemi yapalım.

````sql
UPDATE employee
 SET name = 'Namık Kemal',
 	birthday = '2000-01-09',
	email = 'namık@kemal.com'
 WHERE id = 1;

 UPDATE employee
 SET id= 29,
	birthday = '2000-08-22',
	email = 'salih@amel.com'
 WHERE name = 'Ettie';

 UPDATE employee
 SET id = 10,
	name = 'Alex de Souza',
	email = 'kaptan@alex.com'
 WHERE birthday = '2017-06-16';

 UPDATE employee
 SET id = 10,
	name = 'Evon',
	email = 'evon@answers.com'
 WHERE email = 'evongrollmann1d@answers.com';

 UPDATE employee
 SET id = 1234,
	email = 'test@user.com'
 WHERE id = 22;
````

4. Sütunların her birine göre ilgili satırı silecek 5 adet DELETE işlemi yapalım.

````sql
DELETE FROM employee
 WHERE id = 1;

DELETE FROM employee
 WHERE name = 'Blondell';

DELETE FROM employee
 WHERE birthday = '2017-06-16';

DELETE FROM employee
 WHERE email = 'evongrollmann1d@answers.com';

DELETE FROM employee
 WHERE email = 'aishak16@state.tx.us';
````

---

## ÖDEV 9

1. City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

````sql
SELECT city, country FROM city
 INNER JOIN country ON city.country_id = country.country_id;
````

2.Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

````sql
SELECT payment_id, first_name, last_name FROM customer
 INNER JOIN payment 
 ON customer.customer_id = payment.customer_id;
````

3. Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz INNER JOIN sorgusunu yazınız.

````sql
SELECT rental_id, first_name, last_name FROM customer
 INNER JOIN rental
 ON customer.customer_id = rental.customer_id;
````

---

## ÖDEV 10

1. City tablosu ile country tablosunda bulunan şehir (city) ve ülke (country) isimlerini birlikte görebileceğimiz LEFT JOIN sorgusunu yazınız.

````sql
SELECT city, country FROM city
 LEFT JOIN country
 ON city.city_id = country.country_id;
````

2. Customer tablosu ile payment tablosunda bulunan payment_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz RIGHT JOIN sorgusunu yazınız.

````sql
SELECT payment_id, first_name, last_name FROM customer
 RIGHT JOIN payment
 ON payment.customer_id = customer.customer_id;
````

3. Customer tablosu ile rental tablosunda bulunan rental_id ile customer tablosundaki first_name ve last_name isimlerini birlikte görebileceğimiz FULL JOIN sorgusunu yazınız.

````sql
SELECT rental_id, first_name, last_name FROM customer
 FULL JOIN rental
 ON rental.customer_id = customer.customer_id;
````

---

## ODEV 11

1. Actor ve customer tablolarında bulunan first_name sütunları için tüm verileri sıralayalım.

````sql
(SELECT first_name FROM actor)
 UNION 
 (SELECT first_name FROM customer);
````

2. Actor ve customer tablolarında bulunan first_name sütunları için kesişen verileri sıralayalım.

````sql
(SELECT first_name FROM actor)
 INTERSECT
 (SELECT first_name FROM customer);
````

3. Actor ve customer tablolarında bulunan first_name sütunları için ilk tabloda bulunan ancak ikinci tabloda bulunmayan verileri sıralayalım.

````sql
(SELECT first_name FROM actor)
 EXCEPT
 (SELECT first_name FROM customer);
````
 4. İlk 3 sorguyu tekrar eden veriler için de yapalım.

````sql
(SELECT first_name FROM actor)
 UNION ALL
 (SELECT first_name FROM customer);
````
````sql
(SELECT first_name FROM actor)
 INTERSECT ALL
 (SELECT first_name FROM customer);
````
````sql
(SELECT first_name FROM actor)
 EXCEPT ALL
 (SELECT first_name FROM customer);
````

---

## ÖDEV 12

1. Film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

````sql
SELECT COUNT(*) FROM film
 WHERE length >
 (
	SELECT AVG(length) FROM film
 );
````

2. Film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

````sql 
SELECT COUNT(*) FROM film
 WHERE rental_rate =
 (
	SELECT MAX(rental_rate) FROM film
 );
````

3. Film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.

````sql
SELECT * FROM film
 WHERE film_id = ANY
 (
	SELECT film_id FROM film
	WHERE rental_rate= 
	(SELECT MIN (rental_rate) FROM film)
	AND  replacement_cost= 
	(SELECT MIN (replacement_cost) FROM film)
 );
````

4. Payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

````sql
SELECT * ,
 ( 
	SELECT COUNT(customer_id) 
	FROM payment 
	GROUP BY customer_id
	ORDER BY COUNT(customer_id) DESC
	LIMIT 1
 )
 FROM customer;
````

---