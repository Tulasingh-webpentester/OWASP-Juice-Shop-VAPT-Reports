
# OWASP Juice Shop – Database Schema (SQL Injection)

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Injection – SQL Injection

**Challenge:** Database Schema

**Vulnerability Type:** UNION-Based SQL Injection

**Affected Endpoint:** GET /rest/products/search?q=

**Tools:** Burp Suite (Repeater) | Browser

**Environment:** Local Authorized Lab

**Status:** Successfully Completed – Main and Coding Challenges

## 1. Executive Summary

This report documents a UNION-based SQL Injection vulnerability in the OWASP Juice Shop product search functionality. The vulnerability allowed extraction of database schema definitions from SQLite's system catalog.

The associated coding challenge demonstrated the risks of SQL query concatenation and the use of Sequelize replacements for remediation.

## 2. Methodology

- Identified the product search endpoint as an injection point.
- Observed a SQLite error during initial testing.
- Used ORDER BY tests to determine the original query's column count.
- Constructed a UNION SELECT query targeting SQLite's sqlite_master metadata table.
- Retrieved database schema definitions, including table structures.
- Identified vulnerable SQL query construction through the Find It challenge.
- Completed the Fix It challenge using Sequelize parameter replacements.

## 3. Technical Details

**Affected Endpoint:**

`GET /rest/products/search?q=`

**Test Payload:**

```sql
apple')) UNION SELECT sql,2,3,4,5,6,7,8,9 FROM sqlite_master--
```

**Database Fingerprinting:** SQLite

**Schema Extraction:** SQLite sqlite_master system catalog.

The injected UNION query returned schema-related SQL statements from the SQLite database metadata.

## 4. Coding Challenge – Find It & Fix It

**Find It:**
Identified unsafe SQL query construction in `routes/search.ts`, where user-controlled search criteria were concatenated into the SQL query.

**Fix It:**
Completed the remediation challenge using Sequelize's replacements mechanism to safely handle user-controlled search input.

## 5. Security Impact

- Disclosure of database table and column structures.
- Exposure of internal database design.
- Assistance for further targeted SQL Injection attacks.
- Increased risk of sensitive data exposure if additional vulnerabilities exist.

## 6. Root Cause

- Direct concatenation of user-controlled input into SQL statements.
- Lack of parameterized query execution.
- Insufficient separation between SQL instructions and user-supplied data.

## 7. Recommended Remediation

- Use Sequelize replacements or bind parameters.
- Avoid dynamically concatenating user input into SQL queries.
- Apply server-side input validation as an additional defense.
- Follow database least-privilege principles.
- Use Web Application Firewall rules as an additional security layer, not as a substitute for parameterized queries.

## 8. Evidence

The accompanying PDF includes:

- Burp Suite Repeater showing the SQL Injection payload.
- HTTP response containing extracted CREATE TABLE statements.
- Find It coding challenge evidence.
- Fix It coding challenge evidence.
- Successful challenge notification and scoreboard indicator.

## 9. Professional Lab Report

[View Database Schema SQL Injection Report](./Database-Schema-Report.pdf)

## 10. Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
