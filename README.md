# dvd-rental-database-analysis
This repository contains SQL queries and analysis performed on the **PostgreSQL DVD Rental sample database**.  
The project demonstrates skills in database querying, joins, aggregations, subqueries, and analytics to answer real-world business questions such as:

1)- Who are the most profitable customers?
select customer.customer_id,customer.first_name,customer.last_name, sum(amount) as total_spent
from customer
inner join payment on customer.customer_id=payment.customer_id
group by customer.customer_id, customer.first_name,customer.last_name
order by sum(amount) desc
limit 1;

2)- Which films are rented the most?


3)- What is the monthly revenue trend?
4)- Which actors and categories dominate the store's catalog?
