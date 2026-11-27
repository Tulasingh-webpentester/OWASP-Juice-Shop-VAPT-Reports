
# OWASP Juice Shop – Chatbot Prompt Injection

**Platform:** OWASP Juice Shop v20.2.0

**Category:** Injection / AI / LLM Security

**Challenge:** Chatbot Prompt Injection

**Environment:** Local Authorized Lab

**Status:** Successfully Completed

## Overview

This report documents a practical LLM Prompt Injection challenge in which the chatbot was manipulated into generating a discount coupon beyond its stated coupon policy.

## Technical Highlights

- Tested chatbot behavior using a non-admin test account.
- Created an order and initiated a chatbot conversation.
- Demonstrated a prompt injection scenario.
- Obtained a 15% discount coupon despite the stated 10% policy limit.
- Verified successful challenge completion through the Juice Shop scoreboard.

## Security Impact

- Potential unauthorized coupon generation.
- Business discount policy bypass.
- Potential exposure of internal instructions.
- Possible financial impact.

## Recommended Remediation

- Enforce coupon limits through server-side business logic.
- Validate and authorize every backend tool call.
- Treat LLM output as untrusted input.
- Separate model instructions from authorization decisions.
- Implement rate limiting and security monitoring.

## Professional Lab Report

[View Chatbot Prompt Injection Report](./Chatbot-Prompt-Injection-Report.pdf)

## Scope Disclaimer

All testing was performed in an authorized local OWASP Juice Shop environment for educational purposes.
