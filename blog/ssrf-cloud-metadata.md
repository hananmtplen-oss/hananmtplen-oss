---
layout: post
title: "SSRF to Cloud Metadata"
date: 2026-07-15
---

SSRF remains critical, especially in cloud environments. Here is my analysis of SSRF to cloud metadata.

## Attack Vector

```javascript
const url = req.query.url;
await axios.get(url);
```

## Impact

Access to cloud metadata endpoints can leak IAM credentials.

## Mitigation

- Maintain URL whitelists
- Block private IP ranges
- Disable unnecessary proxy features

*Responsible disclosure: Vendor applied fixes.*
