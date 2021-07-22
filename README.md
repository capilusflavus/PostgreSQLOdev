# PostgreSQLOdev
<a href='#Ödev 1'>Ödev 1</a><br>
<a href='#Ödev 2'>Ödev 2</a><br>
<a href='#Ödev 3'>Ödev 3</a><br>
<a href='#Ödev 4'>Ödev 4</a><br>
<a href='#Ödev 5'>Ödev 5</a><br>
<a href='#Ödev 6'>Ödev 6</a><br>
<a href='#Ödev 7'>Ödev 7</a><br>
<a href='#Ödev 8'>Ödev 8</a><br>
<a href='#Ödev 9'>Ödev 9</a><br>
<a href='#Ödev 10'>Ödev 10</a><br>







## <p id = 'Ödev 1' > Ödev 1 </p> 

#### Örnek 1 :  Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title,description FROM film;
~~~

#### Örnek 2 : Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~sql
SELECT title,length FROM film 
WHERE length>60 and length<75;
~~~

#### Örnek 3 : Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~sql
SELECT title,rental_rate,replacement_cost FROM film 
WHERE replacement_cost=28.99 or replacement_cost=12.99 and rental_rate=0.99;
~~~

#### Örnek 4 : Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
~~~sql
SELECT first_name,last_name FROM customer
WHERE first_name='Mary';
~~~
Cevap = Smith 


#### Örnek 5 : Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~sql
SELECT length,rental_rate FROM film 
WHERE NOT ( rental_rate=0.99 or rental_rate=4.99)AND length<50;
~~~

## <p id = 'Ödev 2' > Ödev 2 </p>

#### Örnek 1 : Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT replacement_cost FROM film 
WHERE replacement_cost BETWEEN 12.99 and 16.99;
~~~

#### Örnek 2 : Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT first_name,last_name FROM actorv 
WHERE  first_name In ('Penolope','Nick','Ed');
~~~

#### Örnek 3 : Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)
~~~sql
SELECT rental_rate, replacement_cost FROM film  
WHERE (rental_rate IN (0.99,2.99,4.99)) AND (replacement_cost IN (12.99,15.99,28.99));
~~~

## <p id = 'Ödev 3' > Ödev 3 </p> 

#### Örnek 1 : Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country FROM country 
HERE country ~~ 'A%a';
~~~

#### Örnek 2 : Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country FROM country 
WHERE country ~~ '_____%n';
~~~

#### Örnek 3 : Film tablosunda bulunan title sütunundaki film isimlerinden en az 4 adet büyük ya da küçük harf farketmesizin 'T' karakteri içeren
~~~sql
SELECT title FROM film 
WHERE title ILIKE '%t%t%t%t%';
~~~

#### Örnek 4 : Film tablosunda bulunan tüm sütunlardaki verilerden title 'C' karakteri ile başlayan ve uzunluğu (length) 90 dan büyük olan ve rental_rate 2.99 olan verileri sıralayınız.
~~~sql
SELECT title,length,rental_rate FROM film 
WHERE (title LIKE 'C%') AND (length>90) AND (rental_rate=2.99);
~~~

## <p id = 'Ödev 4' > Ödev 4 </p> 

#### Örnek 1 : Film tablosunda bulunan replacement_cost sütununda bulunan birbirinden farklı değerleri sıralayınız.
~~~sql
SELECT DISTINCT replacement_cost FROM film;
~~~

#### Örnek 2 : Film tablosunda bulunan replacement_cost sütununda birbirinden farklı kaç tane veri vardır?
~~~sql
SELECT COUNT (DISTINCT replacement_cost) FROM film;
~~~

#### Örnek 3 : Film tablosunda bulunan film isimlerinde (title) kaç tanesini T karakteri ile başlar ve aynı zamanda rating 'G' ye eşittir?
~~~sql
SELECT COUNT (*) FROM film 
WHERE (title LIKE 'T%') AND (rating='G');
~~~

#### Örnek 4 : Country tablosunda bulunan ülke isimlerinden (country) kaç tanesi 5 karakterden oluşmaktadır?
~~~sql
SELECT COUNT (country) FROM country 
WHERE country LIKE ('_____');
~~~

#### Örnek 5 : City tablosundaki şehir isimlerinin kaçtanesi 'R' veya r karakteri ile biter?
~~~sql
SELECT COUNT (*) FROM city 
WHERE city ILIKE ('%r');
~~~


## <p id = 'Ödev 5' > Ödev 5 </p> 

#### Örnek 1 : Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en uzun (length) 5 filmi sıralayınız.
~~~sql
SELECT * FROM film  
WHERE title LIKE '%n' 
ORDER BY length DESC 
LIMIT 5;
~~~

#### Örnek 2 : Film tablosunda bulunan ve film ismi (title) 'n' karakteri ile biten en kısa (length) ikinci 5 filmi sıralayınız.
~~~sql
SELECT * FROM film 
WHERE title LIKE '%n'
ORDER BY length 
OFFSET 5
LIMIT 5;
~~~

#### Örnek 3 : Customer tablosunda bulunan last_name sütununa göre azalan yapılan sıralamada store_id 1 olmak koşuluyla ilk 4 veriyi sıralayınız.
~~~sql
SELECT * FROM customer
WHERE store_id=1
ORDER BY last_name DESC
LIMIT 4;
~~~

## <p id = 'Ödev 6' > Ödev 6 </p> 

#### Örnek 1 : Film tablosunda bulunan rental_rate sütunundaki değerlerin ortalaması nedir?
~~~sql
SELECT ROUND(AVG(rental_rate),3) FROM film;
~~~

#### Örnek 2 : Film tablosunda bulunan filmlerden kaçtanesi 'C' karekteri ile başlar?
~~~sql
SELECT COUNT(*) FROM film
WHERE title LIKE ('C%');
~~~

#### Örnek 3 : Film tablosunda bulunan filmlerden rental_rate değeri 0.99 a eşit olan en uzun (length) film kaç dakikadır?
~~~sql
SELECT MAX (length) FROM film
Where rental_rate=0.99;
~~~

#### Örnek 4 : Film tablosunda bulunan filmlerin uzunluğu 150 dakikadan büyük olanlarına ait kaç farklı replacement_cost değeri vardır?
~~~sql
SELECT COUNT (DISTINCT replacement_cost) FROM film
WHERE  length>150;
~~~

## <p id = 'Ödev 7' > Ödev 7 </p> 

#### Örnek 1 : Film tablosunda bulunan filmleri rating değerlerine göre gruplayınız.
~~~sql
SELECT rating, COUNT(*) FROM film
GROUP BY rating;
~~~

#### Film tablosunda bulunan filmleri replacement_cost sütununa göre grupladığımızda film sayısı 50 den fazla olan replacement_cost değerini ve karşılık gelen film sayısını sıralayınız.
~~~sql
SELECT replacement_cost, COUNT(*) FROM film
GROUP BY replacement_cost
HAVING COUNT(*)>50;
~~~

#### Customer tablosunda bulunan store_id değerlerine karşılık gelen müşteri sayılarını nelerdir?
~~~sql
SELECT store_id,COUNT(*) FROM customer
GROUP BY store_id ;
~~~

#### City tablosunda bulunan şehir verilerini country_id sütununa göre gruplandırdıktan sonra en fazla şehir sayısı barındıra country_id bilgisini ve şehir sayısını paylaşınız.
~~~sql
SELECT country_id, COUNT(*) FROM city
GROUP BY country_id
ORDER BY COUNT(*) DESC
LIMIT 1;

country_id = 44 , count = 60
~~~

## <p id = 'Ödev 8' > Ödev 8 </p>

#### Test veritabanınızda employee isimli sütun bilgileri id(INTEGER), name VARCHAR(50), birthday DATE, email VARCHAR(100) olan bir tablo oluşturalım.
~~~sql












