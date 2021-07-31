1. soru : film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

`` SELECT COUNT(*) FROM film 
WHERE length >
( SELECT  AVG(length)FROM film ) ``


2. soru : film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

`` SELECT COUNT(title) FROM film 
WHERE rental_rate =
( SELECT MAX(rental_rate) FROM film ) ``


3. soru : film tablosunda en düşük rental_rate ve en düşük replacement_cost değerlerine sahip filmleri sıralayınız.

`` SELECT title, rental_rate, replacement_cost FROM film 
WHERE (rental_rate, replacement_cost) IN
( SELECT MIN(rental_rate), MIN(replacement_cost) FROM film ); ``



4. soru : payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.


`` SELECT first_name, last_name FROM customer as c , payment as p
WHERE amount = ANY 
( SELECT MAX(amount)  FROM payment) 
AND c.customer_id = p.customer_id; ``