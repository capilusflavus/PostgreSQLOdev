# PostgreSQLOdev
<a href='#Ödev 1'>Ödev 1</a><br>
<a href='#Ödev 2'>Ödev 2</a><br>
<a href='#Ödev 3'>Ödev 3</a><br>
<a href='#Ödev 4'>Ödev 4</a><br>
<a href='#Ödev 5'>Ödev 5</a><br>
















## <p id = 'Ödev 1' > Ödev 1 </p> 
#### Film tablosunda bulunan title ve description sütunlarındaki verileri sıralayınız.
~~~sql
SELECT title,description FROM film;
~~~

#### Film tablosunda bulunan tüm sütunlardaki verileri film uzunluğu (length) 60 dan büyük VE 75 ten küçük olma koşullarıyla sıralayınız.
~~~sql
SELECT title,length FROM film 
WHERE length>60 and length<75;
~~~

#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99 VE replacement_cost 12.99 VEYA 28.99 olma koşullarıyla sıralayınız.
~~~sql
SELECT title,rental_rate,replacement_cost FROM film 
WHERE replacement_cost=28.99 or replacement_cost=12.99 and rental_rate=0.99;
~~~

#### Customer tablosunda bulunan first_name sütunundaki değeri 'Mary' olan müşterinin last_name sütunundaki değeri nedir?
~~~sql
SELECT first_name,last_name FROM customer
WHERE first_name='Mary';
~~~
Cevap = Smith 


#### Film tablosundaki uzunluğu(length) 50 ten büyük OLMAYIP aynı zamanda rental_rate değeri 2.99 veya 4.99 OLMAYAN verileri sıralayınız.
~~~sql
SELECT length,rental_rate FROM film 
WHERE NOT ( rental_rate=0.99 or rental_rate=4.99)AND length<50;
~~~
## <p id = 'Ödev 2' > Ödev 2 </p> 
#### Film tablosunda bulunan tüm sütunlardaki verileri replacement cost değeri 12.99 dan büyük eşit ve 16.99 küçük olma koşuluyla sıralayınız ( BETWEEN - AND yapısını kullanınız.)
~~~sql
SELECT replacement_cost FROM film 
WHERE replacement_cost BETWEEN 12.99 and 16.99;
~~~
#### Actor tablosunda bulunan first_name ve last_name sütunlardaki verileri first_name 'Penelope' veya 'Nick' veya 'Ed' değerleri olması koşuluyla sıralayınız. ( IN operatörünü kullanınız.)
~~~sql
SELECT first_name,last_name FROM actorv 
WHERE  first_name In ('Penolope','Nick','Ed');
~~~
#### Film tablosunda bulunan tüm sütunlardaki verileri rental_rate 0.99, 2.99, 4.99 VE replacement_cost 12.99, 15.99, 28.99 olma koşullarıyla sıralayınız.(IN operatörünü kullanınız.)
~~~sql
SELECT rental_rate, replacement_cost FROM film  
WHERE (rental_rate IN (0.99,2.99,4.99)) AND (replacement_cost IN (12.99,15.99,28.99));
~~~
## <p id = 'Ödev 3' > Ödev 3 </p> 
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden 'A' karakteri ile başlayıp 'a' karakteri ile sonlananları sıralayınız.
~~~sql
SELECT country FROM country HERE country ~~ 'A%a';
~~~
#### Country tablosunda bulunan country sütunundaki ülke isimlerinden en az 6 karakterden oluşan ve sonu 'n' karakteri ile sonlananları sıralayınız.
~~~sql






















