---
layout: post
title: "Open Redirect Vulnerability Analysis"
date: 2026-07-12
---

Open redirects are often underestimated but can enable powerful phishing attacks.

## Attack Scenarios

### 1. Phishing
```
https://legitimate.com/redirect?url=https://evil.com
```

User sees legitimate domain but is redirected to attacker site.

### 2. OAuth Flow Bypass
Manipulate redirect_uri in OAuth authorization flows.

### 3. JavaScript Injection
Redirect to `javascript:` scheme in some contexts.

## Testing Methodology

- Test `?url=`, `?redirect=`, `?next=`, `?return=`, `?callback=`
- Check for protocol validation
- Test relative paths (`//evil.com`)
- Test URL encoding bypasses

## Impact

- Phishing attacks
- OAuth token theft
- Session hijacking

## Remediation

- Maintain explicit allowlists of redirect destinations
- Disallow external URLs
- Use relative paths only

*Responsible disclosure research.*
