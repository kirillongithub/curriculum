# When to add Indices
author: SebaRaba

levels:

  - beginner

  - basic

type: normal

category: must-know

links:

  - '[SQLMag Dos and Donts of indices](http://sqlmag.com/database-performance-tuning/indexing-dos-and-don-ts)'

---
## Content

Indices[1] are meant to help SQL Servers to lookup data *faster*. However we need to pay attention at how often the data will be inserted, updated and deleted. That is because each time we modify data in an indexed table, the index needs to be updated as well. This can lead to *lower performance* in the end.

Thus, we should bear in mind the followings while creating Indices:
- for tables that have frequent writes, use as few columns as possible under the same index
- if the table contains a lot of data, but the data isn't modified that frequently, use as many Indices to improve performance
- try to select columns with very little data in clustered indices, large columns like `text` cause performance issues
- the more duplicates we have in a column, the lower the performance of the index
- If we use more columns in a single index, the order is important because the table will be primarily sorted by the first index, and secondarily sorted by the second index, and so on


Now, talking about queries' performance on indexed table:
- try to compute as many rows as possible in a single query, rather writing multiple queries
- create non-clustered Indices on columns used frequently in `JOIN` queries
- indexing columns is important when working with exact-match queries
---
## Practice

Consider the "experience" table. We want to create a non-clustered index on the "experience" column:
```
id  | level | experience | growth_rate_id
-----+-------+------------+----------------
  1 |     1 |          0 |              1
  2 |     2 |         10 |              1
  3 |     3 |         33 |              1
  4 |     4 |         80 |              1
  5 |     5 |        156 |              1
  6 |     6 |        270 |              1
  7 |     7 |        428 |              1
  8 |     8 |        640 |              1
  9 |     9 |        911 |              1
 10 |    10 |       1250 |              1
 11 |    11 |       1663 |              1
...

??? INDEX exp_index
??? experience (???)
```

* CREATE
* ON
* experience
* UNIQUE
* INDEX
* level


---
## Revision

Consider the "experience" table. We want to create a non-clustered index on the "experience" column:
```
id  | level | experience | growth_rate_id
-----+-------+------------+----------------
  1 |     1 |          0 |              1
  2 |     2 |         10 |              1
  3 |     3 |         33 |              1
  4 |     4 |         80 |              1
  5 |     5 |        156 |              1
  6 |     6 |        270 |              1
  7 |     7 |        428 |              1
  8 |     8 |        640 |              1
  9 |     9 |        911 |              1
 10 |    10 |       1250 |              1
 11 |    11 |       1663 |              1
...

??? INDEX exp_index
??? experience (???)
```

* CREATE
* ON
* experience
* UNIQUE
* INDEX
* level

---
## Footnotes

[1:Indices]
Reasonable people differ when they refer to the plural of Index. Some people use Indices, some use Indexes.