---
layout: post
title: "CORS Misconfiguration Deep Dive"
date: 2026-07-21
---

CORS misconfigurations can expose sensitive APIs to cross-origin attacks. Here is my analysis of common CORS flaws.

## Reflection Attacks

When `Access-Control-Allow-Origin` reflects the `Origin` header:
```javascript
// Attacker
fetch('https://api.target.com/data', {
  credentials: 'include'
})
```

## Null Origin

Some implementations accept `Origin: null`, which can be triggered from local files or sandboxed iframes.

## Wildcard with Credentials

`Access-Control-Allow-Origin: *` with `Access-Control-Allow-Credentials: true` is invalid but sometimes accepted.

## Impact

- Cross-origin data theft
- Session riding
- API key extraction

## Testing Tools

- Burp Suite CORS scanner
- Custom Origin header manipulation
- Corsy and CorsScan

*Research for defensive purposes.*
