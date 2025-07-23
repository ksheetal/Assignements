
## Assignment 1 : Secure and Structured Logging with Traceability

### Objective:

Implement structured logging in your backend project. Ensure PII (Personally Identifiable Information) is masked, and include traceability metadata in all logs.

---

### What You Need to Do:

1. **Choose any backend project** you’ve worked on or are currently building (e.g., user registration, login, payments, etc.).
2. Add structured logging for key events in the project using a logging library.
3. Mask or remove the following PII fields in all logs:

   * Aadhaar: `********9012`
   * PAN: `A***E1234F`
   * Phone: `*******10`
   * Email: `a****@example.com`
4. Use appropriate log levels: INFO, DEBUG, ERROR, WARN.
5. Structure logs in JSON format.
6. Add **traceability fields** in each log:

   * `timestamp`
   * `requestId` (unique per API call)
   * `userId` (if available)
   * `eventType` (e.g., USER\_REGISTRATION, LOGIN\_ATTEMPT)
   * `serviceName` (name of the service/module)
   * `functionName` (method or route handler name)

---

### Example Input:

```json
{
  "userId": "u123",
  "name": "Amit Sharma",
  "email": "amit.sharma@example.com",
  "phone": "9876543210",
  "aadhaar": "1234-5678-9012",
  "pan": "ABCDE1234F"
}
```

---

### Example Log Output:

```json
{
  "timestamp": "2025-07-23T10:30:00Z",
  "level": "INFO",
  "requestId": "req-456",
  "userId": "u123",
  "eventType": "USER_REGISTRATION",
  "serviceName": "UserService",
  "functionName": "registerUser",
  "message": "User registration completed",
  "payload": {
    "email": "a****@example.com",
    "phone": "*******10",
    "aadhaar": "********9012",
    "pan": "A***E1234F"
  }
}
```

---

### Deliverables:

* Your project with logging implemented
* A `README.md` file that includes:

  * Setup steps
  * How masking and traceability are implemented
  * Sample log output

---

### Notes:

* You can use any backend language and logging framework.
* Do not log full PII under any condition.
* Implement a utility function to sanitize log data.
* Add `requestId` using a middleware or interceptor to support tracing logs across services or API calls.

