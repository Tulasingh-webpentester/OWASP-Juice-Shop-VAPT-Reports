
# OWASP Juice Shop – Server-Side XSS Protection

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Cross-Site Scripting (XSS) – Danger Zone

**Challenge:** Server-Side XSS Protection

**Difficulty:** 4 Stars

**Status:** Successfully Completed

## Overview

This report documents a Stored XSS vulnerability involving a server-side HTML sanitization bypass through the Customer Feedback functionality.

## Technical Highlights

- Submitted crafted nested iframe content through Customer Feedback.
- Completed the CAPTCHA and submitted the feedback.
- Accessed the stored feedback through Administration → Customer Feedback.
- Observed JavaScript execution when the feedback was rendered.
- Verified successful challenge completion.

## Security Impact

Stored XSS may allow attacker-controlled JavaScript to execute in the browsers of users who view affected content.

## Recommended Remediation

- Use a maintained and securely configured HTML sanitization library.
- Apply context-aware output encoding.
- Validate and sanitize user-generated content on the server.
- Configure a restrictive Content Security Policy (CSP).

## Professional Lab Report

[View Server-Side XSS Report](./Server-Side-XSS-Protection-Report.pdf)

## Scope Disclaimer

All testing was performed in an authorized local OWASP Juice Shop environment for educational purposes.
