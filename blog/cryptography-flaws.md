---
layout: post
title: "Common Cryptographic Implementation Flaws"
date: 2026-07-09
---

Weak cryptographic implementations can completely undermine application security.

## Common Flaws

### 1. ECB Mode
AES-ECB is deterministic and reveals patterns:
```javascript
const cipher = crypto.createCipheriv('aes-256-ecb', key, iv);
```

### 2. Static IVs
Reusing IVs with CBC mode compromises security.

### 3. Weak Randomness
Using `Math.random()` for security-critical values.

### 4. Hardcoded Secrets
Embedding keys in source code or configuration files.

## Testing Approach

- Review encryption mode selection
- Check IV generation and randomness
- Analyze key derivation functions
- Test for padding oracle attacks

## Remediation

- Use AES-GCM or AES-CBC with random IVs
- Generate keys using cryptographically secure RNG
- Derive keys from passwords using PBKDF2 or Argon2
- Rotate keys regularly

*Security research documentation.*
