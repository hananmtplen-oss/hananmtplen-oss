---
layout: post
title: "XSS in Single Page Applications"
date: 2026-07-10
---

Modern SPAs introduce unique XSS challenges. This post covers DOM-based XSS in React/Vue/Angular apps.

## Dangerous sink

```javascript
document.getElementById('output').innerHTML = userInput;
```

## Prevention

- Use textContent instead of innerHTML
- Sanitize with DOMPurify
- Implement strong CSP

*Research for defensive security purposes.*
