
## 1. AFTER INSERT Trigger

```sql
CREATE OR REPLACE FUNCTION log_user_insert()
RETURNS TRIGGER AS $$
BEGIN
  INSERT INTO audit_log(action, user_id, action_time)
  VALUES ('insert', NEW.id, NOW());
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER after_user_insert
AFTER INSERT ON users
FOR EACH ROW
EXECUTE FUNCTION log_user_insert();
```

---

## 2. BEFORE UPDATE Trigger

```sql
CREATE OR REPLACE FUNCTION update_timestamp()
RETURNS TRIGGER AS $$
BEGIN
  NEW.updated_at = NOW();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER before_update_users
BEFORE UPDATE ON users
FOR EACH ROW
EXECUTE FUNCTION update_timestamp();
```

---

## 3. AFTER DELETE Trigger

```sql
CREATE OR REPLACE FUNCTION log_user_delete()
RETURNS TRIGGER AS $$
BEGIN
  INSERT INTO audit_log(action, user_id, action_time)
  VALUES ('delete', OLD.id, NOW());
  RETURN OLD;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER after_user_delete
AFTER DELETE ON users
FOR EACH ROW
EXECUTE FUNCTION log_user_delete();
```

---

## 4. BEFORE INSERT Trigger with Validation

```sql
CREATE OR REPLACE FUNCTION validate_email()
RETURNS TRIGGER AS $$
BEGIN
  IF NEW.email !~* '^[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Za-z]{2,}$' THEN
    RAISE EXCEPTION 'Invalid email format';
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER email_validate
BEFORE INSERT ON contacts
FOR EACH ROW
EXECUTE FUNCTION validate_email();
```

---

## 5. AFTER UPDATE Trigger Logging Salary Change

```sql
CREATE OR REPLACE FUNCTION log_salary_change()
RETURNS TRIGGER AS $$
BEGIN
  IF NEW.salary <> OLD.salary THEN
    INSERT INTO salary_log(emp_id, old_salary, new_salary, change_date)
    VALUES (NEW.id, OLD.salary, NEW.salary, NOW());
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER after_salary_update
AFTER UPDATE ON employees
FOR EACH ROW
EXECUTE FUNCTION log_salary_change();
```

---

## 6. BEFORE DELETE Trigger Preventing Deletion

```sql
CREATE OR REPLACE FUNCTION prevent_deletion()
RETURNS TRIGGER AS $$
BEGIN
  RAISE EXCEPTION 'Deletion is not allowed!';
  RETURN OLD;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER prevent_user_delete
BEFORE DELETE ON users
FOR EACH ROW
EXECUTE FUNCTION prevent_deletion();
```

---

## 7. AFTER UPDATE OF Specific Column

```sql
CREATE OR REPLACE FUNCTION log_address_change()
RETURNS TRIGGER AS $$
BEGIN
  IF NEW.address <> OLD.address THEN
    INSERT INTO address_history(user_id, old_address, new_address, changed_at)
    VALUES (NEW.id, OLD.address, NEW.address, NOW());
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER trg_address_update
AFTER UPDATE OF address ON users
FOR EACH ROW
EXECUTE FUNCTION log_address_change();
```

---

## 8. BEFORE INSERT Trigger Setting Default Value

```sql
CREATE OR REPLACE FUNCTION set_default_status()
RETURNS TRIGGER AS $$
BEGIN
  IF NEW.status IS NULL THEN
    NEW.status := 'active';
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER before_insert_set_status
BEFORE INSERT ON accounts
FOR EACH ROW
EXECUTE FUNCTION set_default_status();
```

---

## 9. AFTER UPDATE Trigger for Statement Level Logging

```sql
CREATE OR REPLACE FUNCTION log_update_statement()
RETURNS TRIGGER AS $$
BEGIN
  INSERT INTO update_log(table_name, action_time)
  VALUES (TG_TABLE_NAME, NOW());
  RETURN NULL;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER after_update_statement
AFTER UPDATE ON projects
FOR EACH STATEMENT
EXECUTE FUNCTION log_update_statement();
```

---

## 10. BEFORE INSERT OR UPDATE Trigger Enforcing Uniqueness

```sql
CREATE OR REPLACE FUNCTION enforce_unique_phone()
RETURNS TRIGGER AS $$
DECLARE
  cnt INTEGER;
BEGIN
  SELECT COUNT(*) INTO cnt FROM contacts WHERE phone = NEW.phone AND id <> COALESCE(NEW.id, -1);
  IF cnt > 0 THEN
    RAISE EXCEPTION 'Phone number must be unique';
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

CREATE TRIGGER unique_phone_check
BEFORE INSERT OR UPDATE ON contacts
FOR EACH ROW
EXECUTE FUNCTION enforce_unique_phone();
```