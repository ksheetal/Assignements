## Assignment 3: Build a Secure Login System with Auth, Logging, and PII Protection

### Objective:

Create a secure user login system using authentication and authorization. All user actions must be logged (without exposing any PII), and the system should have proper input validations and security measures.

---

### Requirements:

1. **Authentication and Authorization:**

   * Use one of the following options:

     * Keycloak (via Docker)
     * Auth0 (free tier)
     * Firebase Auth
     * OR build your own basic authentication logic using hashed passwords and role-based access
   * Include login and logout functionality.
   * Support at least two roles: `user` and `admin`.

2. **Input Validation:**

   * Validate email format, password strength, and required fields.
   * Handle invalid or malformed inputs gracefully with error messages.
   * Sanitize inputs to avoid injection or attack vectors.

3. **Logging:**

   * Log all major events (e.g., login attempt, success, failure, logout, access to restricted routes).
   * Logs must be:

     * Structured (preferably JSON)
     * Stored in a database or a file
     * Should not contain any PII (email, name, password, Aadhaar, etc.)
   * Add metadata for traceability:

     * `timestamp`
     * `eventType`
     * `requestId` (generate per request)
     * `userId` (if available)
     * `functionName`
     * `serviceName`

4. **Security:**

   * Passwords must be stored using secure hashing (e.g., bcrypt, Argon2).
   * No raw or plaintext PII should be stored in logs.
   * Use HTTPS locally if possible.
   * Protect routes based on roles.

---

### Deliverables:

* Working backend application (Node.js, Spring Boot, or any other stack).
* Dockerfile and/or `docker-compose.yml` (if using Keycloak or database).
* Sample users and roles setup.
* README with:

  * Setup instructions
  * API documentation (login, logout, protected route)
  * Explanation of validation and logging mechanism
  * Sample log entries (showing no PII)

---

### Optional:

* Add email OTP or multi-factor authentication.
* Add account lockout after failed login attempts.
* Add token expiration and refresh token mechanism.
* Provide Postman collection or Swagger for testing.

---

### Notes:

* You can integrate this assignment with your previous logging assignments.
* If you're using Keycloak or any external identity provider, demonstrate how logs are generated for user actions using Keycloak events.

