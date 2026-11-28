# OWASP Juice Shop – Christmas Special

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Injection – SQL Injection / Business Logic

**Challenge:** Christmas Special

**Vulnerability Type:** SQL Injection | API Parameter Tampering

**Tools:** Burp Suite (Repeater) | Browser

**Affected Endpoints:**
- `GET /rest/products/search?q=`
- `POST /api/BasketItems/`

**Environment:** Local Authorized Lab

**Status:** Successfully Completed

## 1. Executive Summary

This report documents a chained vulnerability involving SQL Injection and API parameter tampering in OWASP Juice Shop.

A hidden, soft-deleted product was retrieved through the product search functionality and subsequently added to the shopping basket by modifying the API request.

## 2. Objective

Identify and exploit weaknesses in product search and basket management to order a discontinued Christmas special product.

## 3. Technical Execution

### A. Product Discovery – SQL Injection

- Identified the product search endpoint as an injection point.
- Tested the search functionality using Burp Suite Repeater.
- Used a UNION-based SQL Injection technique to retrieve hidden product records.
- Identified the Christmas Super-Surprise-Box (2014 Edition).
- Retrieved the product ID associated with the hidden item.

### B. API Parameter Tampering

- Intercepted a `POST /api/BasketItems/` request using Burp Suite.
- Modified the `ProductId` parameter to reference the hidden product.
- Submitted the modified request.
- Verified that the discontinued product was added to the shopping basket.

### C. Checkout and Challenge Verification

- Proceeded through the checkout process.
- Observed successful challenge completion.
- Verified the challenge using the scoreboard completion indicator.

## 4. Vulnerability Details

**Product Search Endpoint:** `GET /rest/products/search?q=`

**Basket API Endpoint:** `POST /api/BasketItems/`

**Manipulated Parameter:** `ProductId`

The testing demonstrated that product visibility and product eligibility were not consistently enforced across the search and basket functionality.

## 5. Security Impact

- Potential ordering of discontinued or restricted products.
- Bypass of intended product availability controls.
- Business logic manipulation through API requests.
- Potential financial and data integrity impact.

## 6. Root Cause

- SQL query construction vulnerable to injection.
- Inconsistent validation of product availability.
- Insufficient server-side verification of product deletion status in basket operations.
- Reliance on frontend visibility restrictions instead of backend enforcement.

## 7. Recommended Remediation

- Use parameterized SQL queries for product searches.
- Validate product availability and deletion status server-side.
- Verify product eligibility before accepting basket requests.
- Enforce consistent business rules across all API endpoints.
- Apply authorization and input validation at the backend.

## 8. Evidence

The accompanying PDF includes:

- Burp Suite Repeater showing the SQL Injection search request.
- HTTP response containing the hidden Christmas product.
- Modified basket API request.
- Shopping cart showing the Christmas special product.
- Order confirmation and successful challenge notification.

## 9. Professional Lab Report

[View Christmas Special SQL Injection Report](./Christmas-Special-Report.pdf)

## 10. Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
