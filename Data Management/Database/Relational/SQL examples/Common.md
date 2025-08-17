
## 1. Creating a Table

```sql
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    username VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## 2. Inserting Data

```sql
INSERT INTO users (username, email)
VALUES ('alice', 'alice@example.com');
```

## 3. Selecting Data

```sql
SELECT * FROM users;
SELECT username, email FROM users WHERE id = 1;
```

## 4. Updating Data

```sql
UPDATE users
SET email = 'alice@newdomain.com'
WHERE id = 1;
```

## 5. Deleting Data

```sql
DELETE FROM users WHERE id = 1;
```

## 6. Adding a Column

```sql
ALTER TABLE users ADD COLUMN is_active BOOLEAN DEFAULT true;
```

## 7. Dropping a Column

```sql
ALTER TABLE users DROP COLUMN is_active;
```

## 8. Creating an Index

```sql
CREATE INDEX idx_users_email ON users(email);
```

## 9. Joining Tables

```sql
SELECT u.username, o.order_total
FROM users u
JOIN orders o ON u.id = o.user_id
WHERE o.order_total > 100;
```

## 10. Aggregate Functions

```sql
SELECT COUNT(*) FROM users;
SELECT AVG(order_total) FROM orders;
SELECT user_id, SUM(order_total) FROM orders GROUP BY user_id;
```

## 11. Limiting and Offsetting Results

```sql
SELECT * FROM users LIMIT 5;
SELECT * FROM users ORDER BY created_at DESC LIMIT 5 OFFSET 10;
```

## 12. Subqueries

```sql
SELECT username FROM users
WHERE id IN (SELECT user_id FROM orders WHERE order_total > 100);
```

## 13. Transactions

```sql
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;
```

## 14. Upsert (INSERT ... ON CONFLICT)

```sql
INSERT INTO users (username, email)
VALUES ('bob', 'bob@example.com')
ON CONFLICT (email) DO UPDATE
SET username = EXCLUDED.username;
```

## 15. Creating a View

```sql
CREATE VIEW active_users AS
SELECT * FROM users WHERE is_active = true;
```
