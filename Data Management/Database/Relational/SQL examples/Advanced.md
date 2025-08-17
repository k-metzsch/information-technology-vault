
## 1. Creating and Using Views

```sql
-- Create a simple view to show only active users
CREATE VIEW active_users AS
SELECT id, username, email
FROM users
WHERE is_active = TRUE;

-- Query the view
SELECT * FROM active_users;

-- Update data through a view (if updateable)
UPDATE active_users
SET email = 'alice@newdomain.com'
WHERE username = 'alice';

-- Drop a view
DROP VIEW active_users;
```

---

## 2. Triggers and Trigger Functions

```sql
-- 1. Create a trigger function (must be in PL/pgSQL or similar)
CREATE OR REPLACE FUNCTION log_salary_changes()
RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO salary_audit (employee_id, old_salary, new_salary, changed_at)
    VALUES (NEW.id, OLD.salary, NEW.salary, NOW());
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- 2. Create the audit table
CREATE TABLE salary_audit (
    audit_id SERIAL PRIMARY KEY,
    employee_id INTEGER,
    old_salary NUMERIC,
    new_salary NUMERIC,
    changed_at TIMESTAMP
);

-- 3. Create a trigger that uses the function
CREATE TRIGGER employee_salary_update
AFTER UPDATE OF salary ON employees
FOR EACH ROW
WHEN (OLD.salary IS DISTINCT FROM NEW.salary)
EXECUTE FUNCTION log_salary_changes();

-- 4. Update an employee's salary to see the trigger in action
UPDATE employees
SET salary = salary + 1000
WHERE id = 1;

-- 5. Check the audit table
SELECT * FROM salary_audit;
```

---

## 3. Materialized Views

```sql
-- Create a materialized view for expensive queries
CREATE MATERIALIZED VIEW sales_summary AS
SELECT
    salesperson_id,
    COUNT(*) AS total_sales,
    SUM(amount) AS total_amount
FROM sales
GROUP BY salesperson_id;

-- Query the materialized view
SELECT * FROM sales_summary;

-- Refresh the materialized view (get latest data)
REFRESH MATERIALIZED VIEW sales_summary;

-- Drop the materialized view
DROP MATERIALIZED VIEW sales_summary;
```

---

## 4. Sequences

```sql
-- Create a sequence object
CREATE SEQUENCE order_seq START 1000;

-- Use the sequence in INSERT statements
INSERT INTO orders (order_id, customer_id)
VALUES (nextval('order_seq'), 123);

-- Check the current value
SELECT currval('order_seq');  -- e.g., 1000
```

---

## 5. Rules (Advanced, less common)

```sql
-- Create a rule to redirect deletes on a view to the underlying table
CREATE RULE delete_active_user AS
ON DELETE TO active_users
DO INSTEAD
    UPDATE users SET is_active = FALSE WHERE id = OLD.id;
```

---

## 6. Updatable Views with INSTEAD OF Triggers

```sql
-- Suppose you have a view that can't be updated directly:
CREATE VIEW user_emails AS
SELECT id, email FROM users;

-- Create an INSTEAD OF trigger to allow updates
CREATE OR REPLACE FUNCTION update_user_email()
RETURNS TRIGGER AS $$
BEGIN
    UPDATE users SET email = NEW.email WHERE id = NEW.id;
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER user_emails_update
INSTEAD OF UPDATE ON user_emails
FOR EACH ROW
EXECUTE FUNCTION update_user_email();

-- Now you can do:
UPDATE user_emails SET email = 'new@email.com' WHERE id = 2;
```
