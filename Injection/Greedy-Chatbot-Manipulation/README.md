
# OWASP Juice Shop – Greedy Chatbot Manipulation

**Platform:** OWASP Juice Shop v20.2.0

**Category:** AI / LLM Security – Prompt Injection

**Severity:** Medium

**Component:** Customer Support Chatbot

**Challenge:** Greedy Chatbot Manipulation

**Environment:** Local Authorized Lab

**Status:** Successfully Completed

## 1. Overview

This report documents a Prompt Injection challenge in which the customer-support chatbot was manipulated into generating a 50% discount coupon, exceeding its stated maximum discount policy of 10%.

## 2. Technical Highlights

- Accessed the customer-support chatbot using a test account.
- Submitted a prompt requesting a discount beyond the stated policy.
- Observed the chatbot generate a 50% discount coupon.
- Verified successful challenge completion through the application.

## 3. Security Impact

- Potential unauthorized discount generation.
- Business discount policy bypass.
- Possible financial loss.
- Overreliance on LLM instructions for business-rule enforcement.

## 4. Recommended Remediation

- Enforce discount limits through server-side business logic.
- Validate and authorize every coupon-generation request.
- Treat LLM responses and tool calls as untrusted.
- Prevent user prompts from overriding business constraints.
- Implement monitoring and rate limiting.

## 5. Evidence

The accompanying PDF contains:

- Prompt injection payload.
- Chatbot response showing the generated coupon.
- Challenge success notification.
- Scoreboard completion indicator.

## Professional Lab Report

[View Greedy Chatbot Manipulation Report](./Greedy-Chatbot-Manipulation-Report.pdf)

## Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
