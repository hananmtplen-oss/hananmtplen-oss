---
layout: post
title: "OAuth 2.0 Security Testing"
date: 2026-07-03
---

OAuth 2.0 implementations often have subtle security flaws.

## Common Issues

### 1. open_redirect in redirect_uri
Some implementations allow redirecting to external URLs after authorization.

### 2. State Parameter Missing
Absence of state parameter enables CSRF attacks.

### 3. Scope Escalation
Requesting broader scopes than intended.

### 4. Token Leakage
Access tokens leaked in referrer headers or browser history.

## Testing Methodology

- Test redirect_uri validation
- Verify state parameter is present and validated
- Check token storage and transmission
- Test refresh token rotation
- Verify PKCE implementation

## Impact

- Account takeover via token theft
- Unauthorized data access
- Session riding

## Remediation

- Validate redirect_uri strictly
- Always use state parameter
- Use PKCE for public clients
- Short-lived access tokens with rotation

*Responsible disclosure research.*
