
# API-Only Cross-Site Scripting (XSS)

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Cross-Site Scripting (XSS)

**Challenge Type:** API Exploitation | Code Analysis | Remediation

**Tools:** Burp Suite (Repeater)

**Status:** Successfully Completed

## Overview

This report documents practical API-only XSS testing through an authenticated API request, source code analysis, and completion of the remediation challenge.

## Technical Highlights

- Modified an authenticated PUT /api/Products/1 request using Burp Suite Repeater.
- Tested an iframe-based XSS payload in the product description.
- Received an HTTP 200 OK response.
- Identified unsafe use of Angular's bypassSecurityTrustHtml method.
- Completed Find It and Fix It (Fix 4) challenges.

## Professional Lab Report

[View API-Only XSS Report](./API-Only-XSS-Report.pdf)

## Scope Disclaimer

All testing was performed in an authorized local OWASP Juice Shop environment for educational purposes.
