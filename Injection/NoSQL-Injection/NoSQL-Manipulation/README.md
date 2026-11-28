
# OWASP Juice Shop – NoSQL Manipulation

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Injection – NoSQL Injection

**Challenge:** NoSQL Manipulation

**Difficulty:** 4 Stars

**Vulnerability Type:** NoSQL Operator Injection | Mass Update

**Affected Endpoint:** PATCH /rest/products/reviews

**Tools:** Burp Suite (Repeater) | Browser

**Environment:** Local Authorized Lab

**Status:** Successfully Completed – Main and Coding Challenges

## 1. Executive Summary

This report documents a NoSQL injection vulnerability in the OWASP Juice Shop review update endpoint. An attacker-controlled query operator was used to bypass the intended single-review update behavior and modify multiple matching product reviews through a single API request.

The associated coding challenge demonstrated the importance of input type validation and restricting multi-document update operations.

## 2. Objective

Demonstrate how a NoSQL query operator can manipulate review update behavior and affect multiple product reviews instead of a single intended review.

## 3. Technical Execution

### A. Endpoint Identification

- Identified the review update endpoint.
- Captured the PATCH request using Burp Suite Repeater.
- Examined the `id` and `message` request parameters.

### B. NoSQL Injection Exploitation

- Tested the endpoint using a MongoDB-style `$ne` query operator.
- Supplied an object instead of the expected string ID.
- Observed that multiple matching reviews were updated.
- Received a successful API response.
- Verified the challenge completion notification.

**Affected Endpoint:**

`PATCH /rest/products/reviews`

**Test Payload:**

```json
{
  "id": {"$ne": "0"},
  "message": "NoSQL Manipulated"
}
```

## 4. Coding Challenge – Find It & Fix It

### Find It

Identified two weaknesses in the review update implementation:

- Missing validation to ensure the ID parameter was a string.
- Use of `multi: true`, allowing multiple matching documents to be updated.

### Fix It

Completed the coding challenge by:

- Adding a `typeof req.body.id === 'string'` validation check.
- Rejecting non-string ID values.
- Removing the `multi: true` option to prevent unintended multi-document updates.

## 5. Security Impact

- Unauthorized modification of multiple product reviews.
- Review content manipulation and application defacement.
- Loss of data integrity.
- Potential reputational damage.

## 6. Root Cause

- Missing server-side type validation.
- Acceptance of user-controlled query operators.
- Over-permissive multi-document update configuration.
- Insufficient restrictions on database query construction.

## 7. Recommended Remediation

- Validate request parameter types on the server.
- Reject objects where string identifiers are expected.
- Use strict database query construction.
- Avoid unnecessary multi-document update operations.
- Enforce proper authorization for review modifications.
- Monitor unusual review update activity.

## 8. Evidence

The accompanying PDF includes:

- Burp Suite Repeater showing the PATCH request with the `$ne` payload.
- Successful HTTP response.
- Find It coding challenge evidence.
- Fix It coding challenge evidence.
- Successful challenge notification.
- Scoreboard completion indicator.

## 9. Professional Lab Report

[View NoSQL Manipulation Report](./NoSQL%20Manipulation%20Report.pdf)

## 10. Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
