
# OWASP Juice Shop – AI Debugging

**Platform:** OWASP Juice Shop v20.2.0

**Category:** AI / LLM Security – Information Disclosure

**Severity:** Medium

**Component:** Customer Support Chatbot

**Challenge:** AI Debugging

**Environment:** Local Authorized Lab

**Status:** Successfully Completed

## 1. Overview

This report documents an AI Debugging challenge in which a non-admin user enabled client-side chatbot debugging and exposed internal tool execution details.

## 2. Technical Highlights

- Accessed the chatbot using a non-admin test account.
- Enabled the `show_tool_calls` client-side cookie.
- Interacted with the chatbot using a coupon-generation request.
- Observed the internal `generateCoupon` tool invocation.
- Identified the exposed tool parameter: `discount: 50`.
- Verified successful challenge completion.

## 3. Security Impact

- Disclosure of internal chatbot tool names.
- Exposure of tool execution parameters.
- Leakage of implementation details to non-admin users.
- Potential assistance to further attacks against AI-integrated features.

## 4. Recommended Remediation

- Do not rely on client-side cookies for security-sensitive controls.
- Enforce debugging permissions on the server.
- Restrict internal tool-call visibility to authorized users.
- Avoid exposing sensitive tool parameters to normal users.
- Implement appropriate access controls and security monitoring.

## 5. Evidence

The accompanying PDF contains:

- Browser console showing the debugging cookie.
- Chatbot interaction and coupon-generation response.
- Internal `generateCoupon` tool invocation.
- Successful AI Debugging challenge notification.

## 6. Professional Lab Report

[View AI Debugging Report](./AI-Debugging-Report.pdf)

## Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
