
## 1. String Functions

```sql
-- LENGTH: Get the number of characters in a string
SELECT LENGTH('PostgreSQL Tutorial');  -- 19

-- LOWER: Convert a string to lowercase
SELECT LOWER('Hello, WORLD!');  -- 'hello, world!'

-- UPPER: Convert a string to uppercase
SELECT UPPER('Hello, world!');  -- 'HELLO, WORLD!'

-- CONCAT: Concatenate multiple strings
SELECT CONCAT('first_', 'second_', 'third');  -- 'first_second_third'

-- SUBSTRING: Extract a substring
SELECT SUBSTRING('database functions', 4, 8);  -- 'abase fu'

-- TRIM: Remove spaces from both ends
SELECT TRIM('   padded string   ');  -- 'padded string'

-- REPLACE: Replace occurrences of a substring
SELECT REPLACE('2025-06-09', '-', '/');  -- '2025/06/09'

-- POSITION: Find the position of a substring
SELECT POSITION('SQL' IN 'PostgreSQL Tutorial');  -- 8

-- SPLIT_PART: Get part of a split string
SELECT SPLIT_PART('apple,banana,cherry', ',', 2);  -- 'banana'
```

---

## 2. Numeric Functions

```sql
-- ABS: Absolute value
SELECT ABS(-123.45);  -- 123.45

-- CEIL: Smallest integer >= number
SELECT CEIL(7.1);  -- 8

-- FLOOR: Largest integer <= number
SELECT FLOOR(7.9);  -- 7

-- ROUND: Round to given decimal places
SELECT ROUND(15.6789, 2);  -- 15.68

-- RANDOM: Random float between 0 and 1
SELECT RANDOM();  -- e.g., 0.549283

-- POWER: Exponentiation
SELECT POWER(5, 3);  -- 125

-- SQRT: Square root
SELECT SQRT(256);  -- 16

-- MOD: Remainder of division
SELECT MOD(22, 6);  -- 4
```

---

## 3. Date & Time Functions

```sql
-- CURRENT_DATE: Today's date
SELECT CURRENT_DATE;  -- 2025-06-09

-- CURRENT_TIME: Current time
SELECT CURRENT_TIME;  -- e.g., 21:10:42.123456

-- CURRENT_TIMESTAMP: Current timestamp
SELECT CURRENT_TIMESTAMP;  -- 2025-06-09 21:10:42.123456+00

-- AGE: Difference between two dates/timestamps
SELECT AGE('2025-12-31', '2024-01-01');  -- 1 year 11 mons 30 days

-- DATE_PART: Extract year, month, day, etc.
SELECT DATE_PART('month', TIMESTAMP '2025-06-09 12:34:56');  -- 6

-- EXTRACT: Same as DATE_PART, but more flexible
SELECT EXTRACT(DOW FROM DATE '2025-06-09');  -- 1 (Monday, where Sunday=0)

-- NOW: Current date and time
SELECT NOW();  -- 2025-06-09 21:10:42.123456+00

-- TO_CHAR: Format date or number as text
SELECT TO_CHAR(TIMESTAMP '2025-06-09 21:15:00', 'Dy, DD Mon YYYY HH24:MI');  
-- 'Mon, 09 Jun 2025 21:15'
```

---

## 4. Aggregate Functions

```sql
-- COUNT: Number of rows
SELECT COUNT(*) FROM employees;  -- 42

-- SUM: Total of a numeric column
SELECT SUM(salary) FROM employees;  -- 287500.00

-- AVG: Average value
SELECT AVG(salary) FROM employees;  -- 6845.24

-- MIN: Smallest value
SELECT MIN(hire_date) FROM employees;  -- 2012-05-17

-- MAX: Largest value
SELECT MAX(salary) FROM employees;  -- 12000.00

-- ARRAY_AGG (Postgres): Collect values into array
SELECT ARRAY_AGG(name) FROM employees WHERE department = 'Sales';
-- {'Alice','Bob','Carol'}

-- STRING_AGG (Postgres): Concatenate strings with separator
SELECT STRING_AGG(name, '; ') FROM employees WHERE hire_date > '2020-01-01';
-- 'Dave; Emma; Frank'
```

---

## 5. Conditional Functions

```sql
-- COALESCE: Return first non-null argument
SELECT COALESCE(NULL, NULL, 'fallback', 'another');  -- 'fallback'

-- NULLIF: Return NULL if arguments are equal, else first argument
SELECT NULLIF('admin', 'admin');  -- NULL
SELECT NULLIF('admin', 'user');   -- 'admin'

-- CASE: Conditional branching in SELECT
SELECT 
  name,
  salary,
  CASE 
    WHEN salary >= 10000 THEN 'high'
    WHEN salary >= 5000  THEN 'medium'
    ELSE 'low'
  END AS salary_band
FROM employees;
-- name  | salary  | salary_band
-- ------|---------|------------
-- Alice | 12000   | high
-- Bob   | 7000    | medium
-- Carol | 3400    | low
```

---

## 6. Array Functions (Postgres)

```sql
-- ARRAY: Construct an array
SELECT ARRAY['red', 'green', 'blue'];  -- {'red','green','blue'}

-- UNNEST: Expand array to set of rows
SELECT UNNEST(ARRAY[101, 102, 103, 104]);
-- 101
-- 102
-- 103
-- 104

-- ARRAY_LENGTH: Get array length
SELECT ARRAY_LENGTH(ARRAY[10, 20, 30, 40, 50], 1);  -- 5

-- ARRAY_APPEND: Add element to array
SELECT ARRAY_APPEND(ARRAY['apple', 'banana'], 'cherry');  -- {'apple','banana','cherry'}
```

---

## 7. JSON Functions (Postgres)

```sql
-- TO_JSON: Convert SQL value to JSON
SELECT TO_JSON(ROW('Alice', 30));  -- '["Alice",30]'

-- TO_JSONB: Convert to binary JSON
SELECT TO_JSONB(ARRAY[1,2,3]);  -- '[1,2,3]'

-- JSONB_BUILD_OBJECT: Build JSON object
SELECT JSONB_BUILD_OBJECT('id', 1, 'name', 'Bob', 'active', true); 
-- '{"id":1,"name":"Bob","active":true}'

-- Access JSON field (-> for JSON, ->> for text)
SELECT '{"name":"Eve","age":25}'::jsonb->'name';   -- '"Eve"'
SELECT '{"name":"Eve","age":25}'::jsonb->>'age';   -- '25'

-- JSONB_ARRAY_ELEMENTS: Unnest a JSON array
SELECT JSONB_ARRAY_ELEMENTS('["a", "b", "c"]'::jsonb);
-- "a"
-- "b"
-- "c"
```

---

## 8. Other Useful Functions

```sql
-- PG_SLEEP: Pause for N seconds (Postgres only)
SELECT PG_SLEEP(2);  -- Waits 2 seconds

-- VERSION: Get PostgreSQL version
SELECT VERSION();  -- 'PostgreSQL 15.0 on x86_64-pc-linux-gnu...'
```