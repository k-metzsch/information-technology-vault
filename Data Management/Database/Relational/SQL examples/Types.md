
## Numeric Types

| Data Type            | Description                  | Example Usage         | Example Value |
| -------------------- | ---------------------------- | --------------------- | ------------- |
| **SMALLINT**         | 2-byte integer               | age SMALLINT          | 18            |
| **INTEGER / INT**    | 4-byte integer               | score INTEGER         | 100           |
| **BIGINT**           | 8-byte integer               | population BIGINT     | 9000000000    |
| **SERIAL**           | Auto-incrementing integer    | id SERIAL PRIMARY KEY | 1, 2, 3, ...  |
| **BIGSERIAL**        | Large auto-increment integer | big_id BIGSERIAL      | 10000000001   |
| **NUMERIC(p,s)**     | Exact precision decimal      | price NUMERIC(10,2)   | 99.99         |
| **DECIMAL(p,s)**     | Alias for NUMERIC            | discount DECIMAL(5,2) | 10.50         |
| **REAL**             | 4-byte floating point        | latitude REAL         | 42.36         |
| **DOUBLE PRECISION** | 8-byte floating point        | temp DOUBLE PRECISION | 98.6          |
| **MONEY**            | Currency amount              | salary MONEY          | $1,000.00     |

---

## Character/String Types

| Data Type         | Description                      | Example Usage            | Example Value      |
|-------------------|----------------------------------|--------------------------|--------------------|
| **CHAR(n)**       | Fixed-length string              | code CHAR(3)             | 'USA'              |
| **VARCHAR(n)**    | Variable-length string           | name VARCHAR(50)         | 'Alice'            |
| **TEXT**          | Unlimited-length string          | comment TEXT             | 'Long text...'     |

---

## Boolean Type

| Data Type         | Description                      | Example Usage        | Example Value   |
|-------------------|----------------------------------|----------------------|-----------------|
| **BOOLEAN**       | True/false value                 | is_active BOOLEAN    | TRUE, FALSE     |

---

## Date/Time Types

| Data Type           | Description                      | Example Usage            | Example Value            |
|---------------------|----------------------------------|--------------------------|--------------------------|
| **DATE**            | Calendar date                    | birthday DATE            | 1990-01-01               |
| **TIME**            | Time of day (no date)            | event_time TIME          | 14:30:00                 |
| **TIME WITH TIME ZONE** / **TIMETZ** | Time with time zone | event_time TIMETZ        | 14:30:00+02              |
| **TIMESTAMP**       | Date and time (no time zone)     | created_at TIMESTAMP     | 2025-06-09 20:00:00      |
| **TIMESTAMP WITH TIME ZONE** / **TIMESTAMPTZ** | Date and time with time zone | login_at TIMESTAMPTZ | 2025-06-09 20:00:00+00   |
| **INTERVAL**        | Time span/duration               | duration INTERVAL        | '3 days', '01:30:00'     |

---

## UUID Type

| Data Type         | Description                      | Example Usage        | Example Value                               |
|-------------------|----------------------------------|----------------------|---------------------------------------------|
| **UUID**          | Universally unique identifier    | uuid UUID            | 'a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11'     |

---

## Array Types

| Data Type  | Description       | Example Usage | Example Value     |
| ---------- | ----------------- | ------------- | ----------------- |
| **TYPE[]** | Array of any type | tags TEXT[]   | {'news','sports'} |

---

## JSON & XML Types

| Data Type         | Description                      | Example Usage        | Example Value                   |
|-------------------|----------------------------------|----------------------|---------------------------------|
| **JSON**          | Textual JSON                     | config JSON          | '{"key": "value"}'              |
| **JSONB**         | Binary JSON (efficient)          | settings JSONB       | '{"enabled": true}'             |
| **XML**           | XML data                         | data XML             | '<note>hello</note>'            |

---

## Geometric Types

| Data Type         | Description                      | Example Usage        | Example Value   |
|-------------------|----------------------------------|----------------------|-----------------|
| **POINT**         | Geometric point (x, y)           | location POINT       | '(1.5,2.5)'     |
| **LINE**          | Infinite line                    | l LINE               | '{1,2,3}'       |
| **CIRCLE**        | Circle (center, radius)          | c CIRCLE             | '<(1,2),3>'     |

---

## Network Address Types

| Data Type         | Description                      | Example Usage        | Example Value       |
|-------------------|----------------------------------|----------------------|---------------------|
| **CIDR**          | IP network                       | net CIDR             | '192.168.1.0/24'    |
| **INET**          | IP address                       | ip INET              | '192.168.1.1'       |
| **MACADDR**       | MAC address                      | mac MACADDR          | '08:00:2b:01:02:03' |

---

## Binary Data Type

| Data Type         | Description                      | Example Usage        | Example Value    |
|-------------------|----------------------------------|----------------------|------------------|
| **BYTEA**         | Binary data                      | file_data BYTEA      | (binary data)    |

---

## Enumerated Types

| Data Type         | Description                      | Example Usage        | Example Value   |
|-------------------|----------------------------------|----------------------|-----------------|
| **ENUM**          | User-defined fixed set           | status status_enum   | 'active'        |
