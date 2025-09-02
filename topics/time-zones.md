# Managing Data in Different Time Zones

Managing data across different time zones is crucial for global applications. Oracle provides robust support for time zone management using specialized data types and functions.

## 1. Time Zone Data Types

- `DATE`: Stores date and time (no time zone)
- `TIMESTAMP`: Stores date and time (no time zone)
- `TIMESTAMP WITH TIME ZONE`: Stores date and time including time zone offset
- `TIMESTAMP WITH LOCAL TIME ZONE`: Stores date and time normalized to the database time zone

## 2. Storing Time Zone Information

```sql
CREATE TABLE transactions (
	txn_id NUMBER,
	account_id NUMBER,
	txn_type VARCHAR2(50),
	txn_time TIMESTAMP WITH TIME ZONE,
	amount NUMBER
);

INSERT INTO transactions VALUES (1001, 20001, 'Deposit', TIMESTAMP '2025-09-02 09:30:00 +01:00', 5000);
INSERT INTO transactions VALUES (1002, 20002, 'Withdrawal', TIMESTAMP '2025-09-02 15:45:00 -05:00', 1200);
```

## 3. Converting Between Time Zones

Use `FROM_TZ`, `AT TIME ZONE`, and `NEW_TIME` to convert between time zones.

```sql
-- Convert a transaction timestamp to a different time zone (e.g., for branch in New York)
SELECT txn_id, txn_time AT TIME ZONE 'America/New_York' AS ny_time
FROM transactions;

-- Assign a time zone to a transaction timestamp (e.g., transaction initiated in Berlin, viewed in Tokyo)
SELECT FROM_TZ(TIMESTAMP '2025-09-02 10:00:00', 'Europe/Berlin') AT TIME ZONE 'Asia/Tokyo' AS tokyo_time
FROM dual;
```

## 4. Retrieving Current Time in a Specific Time Zone

```sql
-- Get current transaction time in UTC (for global audit logs)
SELECT CURRENT_TIMESTAMP AT TIME ZONE 'UTC' AS utc_time FROM dual;

-- Get current transaction time in India (for Indian branch operations)
SELECT CURRENT_TIMESTAMP AT TIME ZONE 'Asia/Kolkata' AS india_time FROM dual;
```

## 5. Handling Daylight Saving Time (DST)

Oracle automatically adjusts for DST when using named time zones (e.g., 'Europe/London'). Always use region names instead of fixed offsets for DST-aware applications.

## 6. Best Practices

- Store timestamps in `TIMESTAMP WITH TIME ZONE` or `TIMESTAMP WITH LOCAL TIME ZONE` for global apps
- Always use named time zones (e.g., 'America/New_York')
- Convert to the user's local time zone in the application or query

---

Proper time zone management ensures accurate transaction processing, reporting, and auditing for banking operations across multiple regions and branches.
