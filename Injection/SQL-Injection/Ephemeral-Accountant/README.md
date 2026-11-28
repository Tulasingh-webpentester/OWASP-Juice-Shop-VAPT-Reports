# OWASP Juice Shop – Ephemeral Accountant (SQL Injection)

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Injection – SQL Injection

**Challenge:** Ephemeral Accountant

**Vulnerability Type:** UNION-Based SQL Injection | Authentication Bypass

**Affected Endpoint:** `POST /rest/user/login`

**Tools:** Burp Suite (Repeater) | Browser Console

**Environment:** Local Authorized Lab

**Status:** Successfully Completed

## 1. Executive Summary

This report documents an SQL Injection vulnerability in the OWASP Juice Shop login functionality. A UNION-based SQL injection technique was used to introduce a synthetic accountant user record into the authentication query result, enabling access without registering that user in the database.

## 2. Objective

Authenticate as the non-existing accountant account `acc0unt4nt@juice-sh.op` without registering the account or knowing an existing user's password.

## 3. Technical Execution

### A. Request Interception

- Captured the login request using Burp Suite.
- Identified `POST /rest/user/login` as the affected endpoint.
- Examined the email and password parameters.

### B. SQL Injection Exploitation

- Crafted a UNION SELECT payload containing literal values.
- Submitted the payload through the email parameter.
- Introduced a synthetic user record with the accounting role into the query result.
- Observed successful authentication as the ephemeral accountant.

### C. Access Verification

- Examined the authentication response.
- Applied the returned authentication token in the local browser.
- Verified access to the Accounting menu.
- Confirmed successful challenge completion.

## 4. Vulnerability Details

**Affected Endpoint:** `POST /rest/user/login`

**Injection Technique:** UNION-Based SQL Injection

**Target Account:** `acc0unt4nt@juice-sh.op`

**Assigned Role:** `accounting`

The test demonstrated that user-controlled input could influence the authentication query result and introduce a non-persistent user record.

## 5. Security Impact

- Authentication bypass.
- Potential unauthorized access to privileged application functionality.
- Role manipulation through SQL query injection.
- Potential exposure of sensitive application information.

The challenge demonstrates that a synthetic user record can be returned by the vulnerable query without being persistently registered in the Users table. This does not mean the activity is undetectable in application or server logs.

## 6. Root Cause

- Unsafe SQL query construction.
- Direct concatenation of user-controlled input.
- Lack of parameterized query execution.
- Insufficient separation between SQL instructions and user data.

## 7. Recommended Remediation

- Use Sequelize bind parameters or replacements.
- Prefer parameterized queries for authentication operations.
- Avoid dynamically concatenating user input into SQL statements.
- Enforce role and authorization checks server-side.
- Apply secure authentication and session management practices.

## 8. Evidence

The accompanying PDF includes:

- Burp Suite Repeater request demonstrating the UNION SELECT test.
- Authentication response with sensitive token information redacted.
- Browser showing the Accounting menu.
- Successful challenge notification.
- Scoreboard completion indicator.

## 9. Professional Lab Report

[View Ephemeral Accountant SQL Injection Report](./Ephemeral-Accountant-Report.pdf)

## 10. Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
