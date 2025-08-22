# dvd-rental-database-analysis
This repository contains SQL queries and analysis performed on the **PostgreSQL DVD Rental sample database**.  
The project demonstrates skills in database querying, joins, aggregations, subqueries, and analytics to answer real-world business questions such as:

1)- Who are the most profitable customers?

solution)-select customer.customer_id,customer.first_name,customer.last_name, sum(amount) as total_spent
from customer
inner join payment on customer.customer_id=payment.customer_id
group by customer.customer_id, customer.first_name,customer.last_name
order by sum(amount) desc
limit 1;

2)- Which films are rented the most?

select film.title, count(rental.rental_id) as rental_count
from film
inner join inventory 
on film.film_id=inventory.inventory_id
inner join rental
ON inventory.inventory_id = rental.inventory_id
group by film.title
order by rental_count desc
limit 10;

3)- What is the monthly revenue trend?

select date_trunc('month',payment.payment_date) as month,
sum(payment.amount) as monthly_revenue
from payment
group by month
order by month;

4)- Which actors and categories dominate the store's catalog?


select actor.actor_id,actor.first_name,actor.last_name,count(film_actor.film_id) as film_count
from actor
inner join film_actor
ON actor.actor_id=film_actor.actor_id
group by actor.actor_id, actor.first_name, actor.last_name
order by film_count desc
limit 10;


5)-Top 10 most rented film?

Solution)-SELECt film.title, count(rental.rental_id)as rental_count
from film
inner join inventory
on film.film_id=inventory.film_id
inner join rental
on inventory.inventory_id=rental.inventory_id
group by film.title
order by rental_count desc
limit 10;
