
# OWASP Juice Shop – NoSQL DoS

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Injection – NoSQL Injection

**Challenge:** NoSQL DoS

**Difficulty:** 4 Stars

**Vulnerability Type:** NoSQL Injection | Denial of Service

**Affected Endpoint:** GET /rest/products/{id}/reviews

**Tools:** Burp Suite (Repeater) | Browser

**Environment:** Local Authorized Lab

**Status:** Successfully Completed

## 1. Executive Summary

This report documents a NoSQL injection vulnerability in the OWASP Juice Shop product review endpoint. A crafted URL path value containing a sleep expression caused the application to delay its response, demonstrating a denial-of-service condition.

## 2. Objective

Demonstrate how an injection vulnerability in the product review endpoint can cause intentional server-side processing delays.

## 3. Technical Execution

### A. Endpoint Identification

- Identified the product review endpoint.
- Captured the request using Burp Suite Repeater.
- Examined the product ID path parameter.

### B. NoSQL Injection Testing

- Tested the endpoint using a sleep expression.
- Injected `sleep(2000)` through the URL path.
- Observed the delayed HTTP response.
- Verified successful challenge completion.

### C. Challenge Verification

- Observed the HTTP response after the intentional delay.
- Confirmed the NoSQL DoS success notification.
- Verified the scoreboard completion indicator.

## 4. Vulnerability Details

**Affected Endpoint:**

`GET /rest/products/{id}/reviews`

**Test Endpoint:**

`GET /rest/products/sleep(2000)/reviews`

**Injection Payload:**

`sleep(2000)`

The challenge demonstrates that user-controlled path input can influence NoSQL query processing and trigger a delay.

The Juice Shop challenge limits the artificial sleep duration to a maximum of two seconds to prevent excessive denial-of-service impact.

## 5. Security Impact

- Intentional delays in application responses.
- Potential service degradation if similar weaknesses are exposed without safeguards.
- Possible resource consumption under repeated concurrent requests.
- Reduced application availability for legitimate users.

## 6. Root Cause

- Insufficient validation of user-controlled path parameters.
- Unsafe handling of input in NoSQL query processing.
- Exposure of database-specific JavaScript expression evaluation.

## 7. Recommended Remediation

- Enforce strict validation of product IDs.
- Accept only expected numeric identifiers.
- Avoid evaluating user-controlled JavaScript expressions.
- Use safe database query interfaces.
- Apply request rate limiting and monitoring.
- Restrict database execution capabilities.

## 8. Evidence

The accompanying PDF includes:

- Burp Suite Repeater request containing the sleep payload.
- HTTP response showing the intentional delay.
- Successful NoSQL DoS challenge notification.
- Scoreboard completion indicator.

## 9. Professional Lab Report

[View NoSQL DoS Report](./NoSQL-DoS-Report.pdf)

## 10. Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
