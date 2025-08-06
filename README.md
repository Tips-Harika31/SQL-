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







