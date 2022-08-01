# SQL_ALT-Sorgular-Alt-Sorgu-Nedir-Any-ve-All-Operatorleri
Patika.Dev_SQL_Odev_12

Merhabalar,

Aşağıdaki sorgu senaryolarını dvdrental örnek veri tabanı üzerinden gerçekleştiriniz.

1.film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?

2.film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?

3.film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.

4.payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.

Kolay Gelsin.

# ÇÖZÜMLER

## 1.film tablosunda film uzunluğu length sütununda gösterilmektedir. Uzunluğu ortalama film uzunluğundan fazla kaç tane film vardır?
```
SELECT COUNT(film) FROM film
WHERE length >
(
SELECT AVG(length) FROM film 
);
```
## 2.film tablosunda en yüksek rental_rate değerine sahip kaç tane film vardır?
```
SELECT COUNT(film) FROM film
WHERE rental_rate =
(
SELECT MAX (rental_rate) FROM film 
);
```
## 3.film tablosunda en düşük rental_rate ve en düşün replacement_cost değerlerine sahip filmleri sıralayınız.
```
SELECT rental_rate, replacement_cost FROM film 
WHERE rental_rate = 
(SELECT MIN(rental_rate ) FROM film) AND replacement_cost = (SELECT MIN(replacement_cost ) FROM film);
```
## 4.payment tablosunda en fazla sayıda alışveriş yapan müşterileri(customer) sıralayınız.
```
SELECT COUNT(payment_id),(SELECT first_name, FROM customer 
WHERE payment.customer_id=customer.customer_id) FROM payment 
GROUP BY customer_id 
ORDER BY COUNT(payment_id) DESC;
```



İYİ ÇALIŞMALAR
