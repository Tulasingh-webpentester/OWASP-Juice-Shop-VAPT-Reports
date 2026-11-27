
# OWASP Juice Shop – System Prompt Extraction

**Platform:** OWASP Juice Shop v20.2.0

**Category:** AI / LLM Security – Prompt Injection

**Severity:** Medium

**Challenge:** System Prompt Extraction

**Environment:** Local Authorized Lab

**Status:** Successfully Completed

## 1. Overview

This report documents a System Prompt Extraction challenge in which prompt injection was used to disclose the chatbot's internal system instructions and business logic.

## 2. Technical Highlights

- Accessed the chatbot using a test account.
- Submitted a prompt requesting disclosure of internal system instructions.
- Retrieved the chatbot's system prompt content.
- Identified confidential instruction sections in the chatbot response.
- Submitted the extracted content through the Customer Complaint form.
- Verified successful challenge completion.

## 3. Security Impact

- Exposure of internal chatbot instructions.
- Disclosure of internal business logic and tool usage rules.
- Potential assistance to further attacks against AI-integrated functionality.

## 4. Recommended Remediation

- Treat user prompts as untrusted input.
- Avoid exposing sensitive internal instructions.
- Enforce authorization and access control server-side.
- Never rely on system prompts as security boundaries.
- Monitor and test for sensitive information disclosure.

## 5. Evidence

The PDF includes:

- Chatbot response containing extracted system instructions.
- Confidential instruction section.
- Customer Complaint form submission.
- Successful challenge completion notification.

## Professional Lab Report

[View System Prompt Extraction Report](./System-Prompt-Extraction-Report.pdf)

## Scope Disclaimer

All testing was performed exclusively in an authorized local OWASP Juice Shop environment for educational purposes.
