## Assignment: Design a Log Storage Database with PII Masking and Traceability

### Objective:

Design a relational database schema to store application logs that are structured, traceable, and secured against PII exposure.

---

### Requirements:

1. **Design the schema** to store logs generated from backend services.
2. Ensure the schema captures:

   * Log metadata
   * Masked payload data
   * Traceability fields
3. PII should not be stored in raw form.
4. Logs must be searchable by requestId, userId, eventType, and timestamp range.

---

### Fields to Store in Log Table:

| Field Name       | Type             | Description                                     |
| ---------------- | ---------------- | ----------------------------------------------- |
| `id`             | UUID / BIGSERIAL | Primary key                                     |
| `timestamp`      | TIMESTAMP        | Time the log was generated                      |
| `level`          | VARCHAR          | Log level (e.g., INFO, ERROR)                   |
| `request_id`     | VARCHAR          | Unique ID for the API call or request           |
| `user_id`        | VARCHAR          | Masked or partial ID of the user (if available) |
| `event_type`     | VARCHAR          | Event category (e.g., USER\_REGISTRATION)       |
| `service_name`   | VARCHAR          | Name of the service/module                      |
| `function_name`  | VARCHAR          | Method or route handler that generated the log  |
| `message`        | TEXT             | Short message for the log entry                 |
| `masked_payload` | JSONB            | Masked PII data as JSON                         |
| `created_at`     | TIMESTAMP        | Time the log was stored in DB (default now())   |

---

### Example Table Creation (PostgreSQL):

```sql
CREATE TABLE application_logs (
  id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
  timestamp TIMESTAMP NOT NULL,
  level VARCHAR(20) NOT NULL,
  request_id VARCHAR(100) NOT NULL,
  user_id VARCHAR(100),
  event_type VARCHAR(100),
  service_name VARCHAR(100),
  function_name VARCHAR(100),
  message TEXT,
  masked_payload JSONB,
  created_at TIMESTAMP DEFAULT NOW()
);

CREATE INDEX idx_logs_request_id ON application_logs(request_id);
CREATE INDEX idx_logs_user_id ON application_logs(user_id);
CREATE INDEX idx_logs_event_type ON application_logs(event_type);
CREATE INDEX idx_logs_timestamp ON application_logs(timestamp);
```

---

### Deliverables:

* Database schema script (SQL)
* Sample `INSERT` statements with masked data
* ER diagram (optional)
* Short explanation of:

  * Why PII is masked
  * How traceability is supported
  * Indexing strategy for querying logs

---

### Notes:

* You may use any relational DB (PostgreSQL preferred).
* Do **not** store unmasked Aadhaar, PAN, phone, or email.
* Store `masked_payload` as a JSON object for flexibility.
* Design for future scalability (e.g., partitions or archiving if needed).

