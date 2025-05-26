# Table of Contents: LeetCode Top SQL 50 Study Plan

1. [Recyclable and Low Fat Products](#problem-1)
2. [Find Customer Referee](#problem-2)
3. [Big Countries](#problem-3)
4. [Article Views I](#problem-4)
5. [Invalid Tweets](#problem-5)
6. [Replace Employee ID With The Unique Identifier](#problem-6)
7. [Product Sales Analysis I](#problem-7)
8. [Customer Who Visited but Did Not Make Any Transactions](#problem-8)
9. [Rising Temperature](#problem-9)
10. [Average Time of Process per Machine](#problem-10)
11. [Employee Bonus](#problem-11)
12. [Students and Examinations](#problem-12)
13. [Managers with at Least 5 Direct Reports](#problem-13)
14. [Confirmation Rate](#problem-14)
15. [Not Boring Movies](#)
16. [Average Selling Price](#)
17. [Project Employees I](#)
18. [Percentage of Users Attended a Contest](#)
19. [Queries Quality and Percentage](#)
20. [Monthly Transactions I](#)
21. [Game Play Analysis I](#)
22. [Number of Unique Subjects Taught by Each Teacher](#)
23. [User Activity for the Past 30 Days I](#)
24. [Product Sales Analysis II](#)
25. [Fix Names in a Table](#)
26. [Group Sold Products By The Date](#)
27. [Patients With a Condition](#)
28. [Second Highest Salary](#)
29. [Department Highest Salary](#)
30. [Swap Salary](#)
31. [Delete Duplicate Emails](#)
32. [Rearrange Products Table](#)
33. [Tree Node](#)
34. [Customers Who Bought All Products](#)
35. [Department Top Three Salaries](#)
36. [Game Play Analysis IV](#)
37. [Find the Subtasks That Did Not Execute](#)
38. [Employees With Missing Information](#)
39. [Find Total Time Spent by Each Employee](#)
40. [Consecutive Numbers](#)
41. [Product Sales Analysis III](#)
42. [Restaurant Growth](#)
43. [Friend Requests II: Who Has the Most Friends](#)
44. [Investments in 2016](#)
45. [Exchange Seats](#)
46. [Movie Rating](#)
47. [Ads Performance](#)
48. [Employees Whose Manager Left the Company](#)
49. [Customers Who Bought Products A and B but Not C](#)
50. [All Valid Triplets That Can Represent a Country](#)


## Problem 1
```sql
SELECT product_id 
FROM Products
WHERE low_fats  = 'Y' AND recyclable = 'Y'
```

## Problem 2
```sql
SELECT name
FROM CUSTOMER
WHERE referee_id IS NULL OR referee_id != 2  
```

## Problem 3
```sql
SELECT name, population, area
FROM WORLD
WHERE  area >= 3000000 OR population >= 25000000
```

## Problem 4
```sql
SELECT DISTINCT viewer_id  AS ID
FROM VIEWS
WHERE AUTHOR_ID = VIEWER_ID
```

## Problem 5
```sql
SELECT TWEET_ID
FROM TWEETS
WHERE LEN(CONTENT) > 15
```
---
# Basic Joins

## Problem 6
```sql
SELECT UNIQUE_ID, NAME
FROM EmployeeUNI
RIGHT JOIN Employees ON Employees.ID=EmployeeUNI.ID
```

## Problem 7
```sql
SELECT PRODUCT_NAME, YEAR, PRICE
FROM PRODUCT AS P
INNER JOIN SALES S ON S.PRODUCT_ID=P.PRODUCT_ID
```

## Problem 8
```sql
SELECT CUSTOMER_ID, COUNT(CUSTOMER_ID) AS count_no_trans 
FROM VISITS
LEFT JOIN Transactions ON VISITS.VISIT_ID = Transactions.VISIT_ID
WHERE Transactions.VISIT_ID IS NULL
GROUP BY CUSTOMER_ID
```

## Problem 9
```sql
SELECT W1.ID
FROM WEATHER AS W1
FULL OUTER JOIN WEATHER AS W2 ON W1.ID = W2.ID
WHERE (DATEDIFF(DAY, W1.recordDate, W2.recordDate)=1 AND W1.temperature > W2.temperature)
```

## Problem 10
```sql
SELECT A1.machine_id, round(AVG(A2.timestamp  - A1.timestamp ), 3) AS processing_time 
FROM Activity  A1
INNER JOIN Activity  A2 ON A1.machine_id =A2.machine_id  AND A1.process_id = A2.process_id
WHERE A1.activity_type='start' AND A2.activity_type='end'
GROUP BY A1.machine_id
```

## Problem 11
```sql
select name, bonus
from employee e
left join bonus b on b.empid=e.empid
where b.bonus < 1000 or b.bonus is null
```

## Problem 12
```sql
select s.student_id, student_name, u.subject_name, count(e.student_id) as attended_exams 
from Students s
cross join Subjects u
left join Examinations e on s.student_id = e.student_id and u.subject_name = e.subject_name
group by s.student_id, student_name, u.subject_name
order by s.student_id , subject_name 
```

## Problem 13

```sql
select name
from employee
where  id  in ((select e1.id 
from employee e1
inner join employee e2 on e1.id=e2.managerid
group by e1.id
having count(e1.id) >= 5))
```

## Problem 14
```sql
select s.user_id, round(avg(case when action='confirmed' then 1.0 else 0.0 end), 2) as confirmation_rate
from signups s
left join confirmations c on s.user_id = c.user_id
group by s.user_id
```