
# OWASP Juice Shop – Login Bender (SQL Injection)

**Platform:** OWASP Juice Shop v20.2.0

**Category:** SQL Injection

**Challenge:** Login Bender

**Vulnerability Type:** Authentication Bypass

**Tools:** Browser | Burp Suite (Optional)

**Environment:** Local Authorized Lab

**Status:** Successfully Completed – Main Challenge and Coding Challenge

## 1. Executive Summary

This report documents an SQL Injection vulnerability in the OWASP Juice Shop login functionality. The vulnerability allowed authentication as the Bender test account without knowing its password.

The associated coding challenge demonstrated the vulnerable SQL query and the use of parameter binding as a remediation.

## 2. Objective

Identify and exploit an SQL Injection vulnerability in the login functionality and complete the associated Find It and Fix It coding challenges.

## 3. Technical Execution

### A. Target Identification

- Identified Bender as the challenge target.
- Used the lab account email: `bender@juice-sh.op`.

### B. SQL Injection Exploitation

- Navigated to the login page.
- Entered the SQL comment payload in the email field:

`bender@juice-sh.op'--`

- Entered an arbitrary test string in the password field.
- Successfully authenticated as the Bender test account.

### C. Coding Challenge – Find It

- Examined the login-related source code.
- Identified unsafe SQL query construction using user-controlled input.
- Located the vulnerable query in the challenge interface.

### D. Coding Challenge – Fix It

- Selected the parameter-binding remediation.
- Used Sequelize's `bind` mechanism to separate SQL instructions from user-supplied values.
- Successfully completed the Fix It challenge.

## 4. Vulnerability Details

**Affected Endpoint:** `POST /rest/user/login`

**Injection Point:** Email parameter

**Test Payload:**

`bender@juice-sh.op'--`

The SQL comment sequence caused the remaining password condition to be ignored in the vulnerable query, resulting in authentication bypass.

## 5. Security Impact

- Unauthorized account access.
- Potential authentication bypass.
- Exposure of account-related information.
- Risk to other accounts if the same vulnerability affects the authentication endpoint.

## 6. Root Cause

- Direct concatenation of user-controlled input into SQL queries.
- Lack of parameterized query execution.
- Insufficient separation between SQL instructions and user-supplied data.

## 7. Recommended Remediation

- Use parameterized queries or prepared statements.
- Apply Sequelize bind parameters for user-supplied values.
- Avoid dynamically concatenating user input into SQL statements.
- Implement appropriate authentication and access controls.
- Use input validation as an additional security layer.

## 8. Evidence

The accompanying PDF includes:

- Login form showing the SQL Injection test payload.
- Successful authentication as the Bender test account.
- Find It coding challenge evidence.
- Fix It coding challenge evidence.
- Challenge completion notification and scoreboard indicator.

## 9. Professional Lab Report

[View Login Bender SQL Injection Report](./Login-Bender-Report.pdf)

## 10. Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
