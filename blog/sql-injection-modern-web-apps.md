---
layout: post
title: "SQL Injection in Modern Web Applications"
date: 2026-07-20
---

SQL injection remains one of the most critical vulnerabilities in web applications. During a recent assessment, I discovered a SQL injection flaw that allowed full database extraction.

## Vulnerability

```sql
SELECT * FROM users WHERE name = 'INPUT'
```

## Impact

- Unauthorized data access
- Authentication bypass
- Potential remote code execution in some configurations

## Remediation

Use parameterized queries:

```python
cursor.execute("SELECT * FROM users WHERE name = ?", (name,))
```

*Disclosed responsibly. Vendor patched within 90 days.*
