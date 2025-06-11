# CSRF 
Cross-Site Request Forgery (CSRF) is an attack that tricks a logged-in user into performing unwanted actions on a web application without their consent, using their authenticated session.

# How does it work?
1. The victim is logged into a target site (e.g., bank.com).
2. The attacker sends the victim a malicious link or form (via email, blog, forum, etc.).
3. When the victim clicks or loads it, the browser automatically sends session cookies, and the request gets processed as if the user made it themselves.


# Key Characteristics of CSRF
1. Exploits trusted user sessions.
2. Does not require stealing cookies or credentials.
3. Happens in authenticated contexts.
4. Often uses hidden forms or auto-submitted requests.


# What is the difference between XSS and CSRF?
Cross-site scripting (or XSS) allows an attacker to execute arbitrary JavaScript within the browser of a victim user.
Cross-site request forgery (or CSRF) allows an attacker to induce a victim user to perform actions that they do not intend to. 


# How to Mitigate CSRF
1.  CSRF Tokens
- Generate a unique token per session/request, and verify it server-side.
2. SameSite Cookie Attribute
- Set cookies with SameSite=Lax or Strict to restrict cross-site usage.
3. Check Origin or Referer Headers
- Validate that requests come from the same site.
4. Use Secure HTTP Methods
- Avoid using GET for state-changing actions. Use POST/PUT/DELETE.


# How to Detect CSRF (as a Pentester)
1. Look for endpoints that change user data or perform sensitive actions:
- Profile updates (/update-profile)
- Password changes (/change-password)
- Transfers (/transfer-money)
- Deleting content (/delete-post)
2. Check if SameSite is missing on cookies
3. Try Burp Suite’s CSRF PoC Generator
- Intercept → Right-click → Generate CSRF PoC → Execute in browser











