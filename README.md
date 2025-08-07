# SQL 
https://leetcode.com/problems/department-highest-salary/

select 
d.name as department, e.name as employee, e.salary as salary 
from employee e 
join department d 
on e.departmentid=d.id 
where e.salary = (select max(salary) from employee where departmentid = e.departmentid)
; 
Corelated subquery:
It joins the employee and department tables.
For each employee, it checks:
Is their salary equal to the maximum salary in their department?
If yes, it returns that employee (i.e., they are the top earner in their department).

https://leetcode.com/problems/rank-scores/description/
select score, dense_rank() over(order by score desc) as 'rank'
from scores
order by score desc;
DENSE_RANK() assigns a ranking to each score based on descending order.
Ties get the same rank, but next rank is not skipped (unlike RANK()).
The ORDER BY score DESC ensures higher scores get lower rank numbers (e.g., 1 is the highest). 

https://leetcode.com/problems/daily-leads-and-partners/
select date_id, make_name, count(distinct lead_id) as unique_leads, count(distinct partner_id) as unique_partners from dailysales group by date_id, make_name;  
Groups the rows by date_id and make_name.
Within each group:
COUNT(DISTINCT lead_id) computes how many unique leads appear.
COUNT(DISTINCT partner_id) computes how many unique partners appear.
Returns one row per (date_id, make_name) pair with the distinct counts.

https://leetcode.com/problems/customer-placing-the-largest-number-of-orders/

select customer_number 
from orders 
group by customer_number
having count(order_number)= 
(select count(order_number) cnt 
from orders group by customer_number
order by cnt desc limit 1); 









