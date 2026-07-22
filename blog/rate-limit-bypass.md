---
layout: post
title: "Rate Limiting Bypass Techniques"
date: 2026-07-19
---

Rate limiting is often implemented incorrectly. This post covers bypass techniques I encountered during assessments.

## Common Bypasses

### 1. IP Rotation
Use X-Forwarded-For header if the application trusts it:
```
X-Forwarded-For: 1.2.3.4
```

### 2. Parameter Pollution
Send multiple values for the same parameter:
```
POST /api/login
username=admin&username=admin&username=admin
```

### 3. Endpoint Substitution
Rate limit on `/api/login` but not `/api/v1/login` or `/api/v2/login`.

### 4. Case Sensitivity
Rate limit on `/login` but not `/LOGIN` or `/LogIn`.

## Impact

- Credential stuffing attacks
- Brute-force password cracking
- API abuse

## Remediation

- Implement rate limiting at multiple layers
- Use consistent endpoint normalization
- Combine with CAPTCHAs and MFA

*Part of responsible disclosure research.*
