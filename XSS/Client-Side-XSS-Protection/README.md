
# Cross-Site Scripting (XSS) – Client-Side XSS Protection

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Cross-Site Scripting (XSS)

**Challenge Type:** Exploitation | Client-Side Protection Bypass

**Tools:** Burp Suite (Proxy – Intercept)

**Status:** Successfully Completed

## Overview

This report documents the bypass of a client-side security mechanism by intercepting and modifying a user registration request using Burp Suite.

## Technical Highlights

- Intercepted the POST /api/Users registration request.
- Modified the email parameter with an iframe-based XSS payload.
- Forwarded the modified request to the application.
- Verified successful challenge completion.

## Security Observations

Client-side validation alone is insufficient because intercepted HTTP requests can be modified before reaching the server.

## Professional Lab Report

[View Client-Side XSS Protection Report](./Client-Side-XSS-Protection-Report.pdf)

## Scope Disclaimer

All testing was performed in an authorized local OWASP Juice Shop environment for educational purposes.
