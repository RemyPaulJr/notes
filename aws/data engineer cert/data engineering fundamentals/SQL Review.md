Aggregation:
```sql
COUNT
SELECT COUNT(*) AS total_rows FROM employees;

SUM
SELECT SUM(salary) AS total_salary

AVG
SELECT AVG(salary) AS average_salary FROM employees;

MAX / MIN
SELECT MIN(salary) AS lowest_salary FROM employees;
```

Aggregate with CASE
- WHERE clauses are specified after aggregation, so you can only filter on one thing at a time.
```sql
SELECT COUNT(*) AS high_salary_count
FROM employees
WHERE salary > 70000;
```
- One way to apply multiple filters to what you're aggregating
```sql
SELECT
	COUNT(CASE WHEN salary > 70000 THEN 1 END) AS high_salary_count,
	COUNT(CASE WHEN salary BETWEEN 50000 AND 70000 THEN 1 END) AS medium_salary_count,
	COUNT(CASE WHEN salary < 50000 THEN 1 END) AS low_salary_count
FROM employees;
```

Grouping
```sql
SELECT department_id, COUNT(*) AS number_of_employees
FROM employees
WHERE join_date > '2020-01-01'
GROUP BY department_id;
```
```diff
department_id | number_of_employees
HR            | 5
IT            | 8
```

Nested grouping, sorting
```sql
SELECT YEAR(sale_date) AS sale_year, product_id, SUM(amount) AS total_sales
FROM sales
GROUP BY sale_year, product_id
ORDER BY sale_year, total_sales DESC;
```
```diff
sale_year | product_id | total_sales
2021      | P001       | 5000
2021      | P002       | 4000
```

Pivoting
- Pivoting is the act of turning row-level data into columnar data.
- How this works is very database-specific. Some have PIVOT command.
- The same thing could be achieved with conditional aggregation, without requiring a specific PIVOT operation.

**JOIN TYPES will be covered**

**SQL Regular Expressions**
- Pattern Matching
	- Think a much more powerful "LIKE"
- ~ is the regular expression operator
- ~* is case-insensitive
- !~* would mean "not match expression, case insensitive"
- Regular expression 101
	- ^ - match a pattern at the start of a string
	- $ - match a pattern at the end of a string (boo$ would match boo but not book)
	- | - alternate characters (sit|sat matches both sit and sat)
	- Ranges ([a-z] matches any lower case letter)
	- Repeats ([a-z]{4} matches any four-letter lowercase word)
	- Special metacharacters
		- \d - any digit; \w - any letter, digit, or underscore, \s - whitespace, \t - tab
	- Example:
		- SELECT * FROM name WHERE name ~ * '^(fire|ice)';
		- Selects any rows where name start with "fire" or "ice" (case-insensitive)