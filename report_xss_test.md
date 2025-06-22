## Reflected XSS Vulnerability – ilunara.com

**Location:** Username field during account registration  
**Payload Used:** `"><script>alert('XSS')</script>`  
**Execution Point:** Dashboard welcome text (post-login)

**Impact:**  
The application reflects unsanitized input directly into the DOM without proper encoding or filtering. This introduces a serious risk of Cross-Site Scripting (XSS), which could be exploited by attackers to:
- Steal session tokens
- Hijack user sessions
- Deface UI
- Redirect users to malicious domains

**Recommendation:**  
- Sanitize all input fields
- Encode user input before rendering to DOM
- Implement a Content Security Policy (CSP)

![Image](https://github.com/user-attachments/assets/31b64d8f-e331-41cd-9edb-e4c11d7a79bc)
![Image](https://github.com/user-attachments/assets/3333d55c-31f2-4343-b56b-3d9635a8a5c4)
