---
layout: post
title: "Path Traversal Vulnerability Testing"
date: 2026-07-07
---

Path traversal (directory traversal) allows attackers to access files outside the intended directory.

## Payload Variations

### Basic Traversal
```
../../../etc/passwd
..%2f..%2f..%2fetc%2fpasswd
..\..\..\windows\win.ini
```

### Windows Paths
```
C:\windows\win.ini
C:\windows\system.ini
```

### Bypass Techniques
- URL encoding
- Double URL encoding
- Null byte injection (older systems)
- Path normalization bypass

## Testing Locations

- File download features
- Image/video uploads
- Template engines
- Log file access
- Backup file downloads

## Impact

- Source code disclosure
- Configuration file access
- Credential theft
- Remote code execution (in some cases)

## Remediation

- Validate and sanitize all file paths
- Use allowlists for file names
- Resolve to absolute paths and verify prefix
- Run with minimal filesystem permissions

*Disclosed responsibly.*
