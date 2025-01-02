# Table of Contents: LeetCode Top SQL 50 Study Plan

1. [Recyclable and Low Fat Products](#problem-1)
2. [Find Customer Referee](#problem-2)
3. [Big Countries](#problem-3)
4. [Article Views I](#problem-4)
5. [Invalid Tweets](#problem-5)
6. [Replace Employee ID With The Unique Identifier](#problem-6)
7. [Product Sales Analysis I](#problem-7)
8. [Customer Who Visited but Did Not Make Any Transactions](#)
9. [Rising Temperature](#)
10. [Average Time of Process per Machine](#)
11. [Employee Bonus](#)
12. [Students and Examinations](#)
13. [Managers with at Least 5 Direct Reports](#)
14. [Confirmation Rate](#)
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