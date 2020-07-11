---
title: leetcode第595题：大国家
tags:
	- leetcode
	- MySQL
categories:
	- leetcode
	- leetcode_easy
	- MySQL
---

###### leetcode第595题：大国家

找出MySQL world表中的大国家，领土大于3百万平方公里或者人口大于2.5千万.

```python
"""
There is a table World

+-----------------+------------+------------+--------------+---------------+
| name            | continent  | area       | population   | gdp           |
+-----------------+------------+------------+--------------+---------------+
| Afghanistan     | Asia       | 652230     | 25500100     | 20343000      |
| Albania         | Europe     | 28748      | 2831741      | 12960000      |
| Algeria         | Africa     | 2381741    | 37100000     | 188681000     |
| Andorra         | Europe     | 468        | 78115        | 3712000       |
| Angola          | Africa     | 1246700    | 20609294     | 100990000     |
+-----------------+------------+------------+--------------+---------------+

A country is big if it has an area of bigger than 3 million square km or a population of more than 25 million.
Write a SQL solution to output big countries' name, population and area.
For example, according to the above table, we should output:
"""
```


```mysql
# Write your MySQL query statement below

SELECT name, population, area
FROM world
WHERE area > 3000000 or population > 25000000;
```
