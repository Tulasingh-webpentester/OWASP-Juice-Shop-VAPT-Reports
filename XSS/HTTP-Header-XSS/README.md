
# HTTP Header-Based Cross-Site Scripting (XSS)

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Cross-Site Scripting (XSS)

**Challenge Type:** HTTP Header Injection | XSS Exploitation

**Tool:** Burp Suite

**Status:** Successfully Completed

## Overview

This report documents the HTTP Header XSS challenge, involving the modification of a custom HTTP header using Burp Suite.

## Technical Highlights

- Intercepted an HTTP request using Burp Suite.
- Added a custom True-Client-IP header.
- Injected an HTML-based XSS payload.
- Received an HTTP 200 OK response.
- Verified successful challenge completion.

## Security Observation

Improper handling of untrusted HTTP header values can introduce XSS vulnerabilities when header-derived data is rendered without appropriate output encoding or sanitization.

## Recommended Remediation

- Never trust client-supplied HTTP headers.
- Apply context-aware output encoding.
- Validate and safely handle header-derived data.
- Avoid rendering untrusted header values as HTML.

## Professional Lab Report

[View HTTP Header XSS Report](./HTTP-Header-XSS-Report.pdf)

## Scope Disclaimer

All testing was performed in an authorized local OWASP Juice Shop environment for educational purposes.
