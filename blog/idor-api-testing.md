---
layout: post
title: "IDOR Vulnerability Testing in REST APIs"
date: 2026-07-22
---

Insecure Direct Object Reference (IDOR) remains one of the most common API vulnerabilities. This post documents my methodology for identifying and exploiting IDOR flaws.

## Testing Methodology

### 1. Parameter Enumeration
Look for numeric IDs in URLs and API responses:
- `/api/users/123`
- `/api/orders/456`
- `/api/invoices/789`

### 2. Horizontal Privilege Escalation
Test if User A can access User B resources by changing the ID parameter.

### 3. Vertical Privilege Escalation
Test if regular users can access admin endpoints.

## Example Vulnerability

```
GET /api/users/12345
Authorization: Bearer <user_token>
```

Changing user ID to 12346 returns another user's profile with PII.

## Impact

- Data leakage
- Account takeover
- Business logic bypass

## Remediation

- Implement proper authorization checks on every request
- Use UUIDs instead of sequential IDs
- Verify resource ownership before access

*Disclosed responsibly. Vendor patched.*
