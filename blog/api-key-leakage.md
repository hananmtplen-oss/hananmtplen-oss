---
layout: post
title: "API Key Leakage in Client-Side Bundles"
date: 2026-07-05
---

API keys embedded in JS bundles are a common high-severity finding.

## Detection

- Inspect .js.map files
- Search for patterns: `sk_`, `AKIA`, `ghp_`
- Use trufflehog on repositories

## Impact

Exposed keys can lead to account takeover and data breaches.

*Published as part of responsible disclosure.*
