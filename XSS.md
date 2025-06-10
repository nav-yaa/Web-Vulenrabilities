# XSS -  Cross Site Scripting 
Cross-Site Scripting (XSS) is a vulnerability that allows attackers to inject malicious scripts into web pages viewed by other users. These scripts usually run in the victim’s browser and can steal cookies, session tokens, or other sensitive information. Its very severe as it can lead to account takeovers
Why is it so prevalant?
1. Web apps rely heavily on user inputs — comments, forms, search bars, URLs, etc. If even one input is unsanitized or unescaped, XSS can creep in.
2. Developers often trust user input, Many apps reflect input back to users without escaping it. If the input isn't properly sanitized or encoded.
3. JavaScript is Powerful JS can read cookies, redirect users


# What are the types of XSS?
1. Stored -
The malicious script is permanently saved on the server — in a database, log file, comment section, etc. Whenever a user accesses that data, the script is executed in their browser.
Example:
A user posts a comment on a blog like: <script>alert('XSS');</script>
If the website does not sanitize this input, then every visitor who reads the comment will see the alert pop up (or worse — whatever the js is intended to do).
Impact:
Affects multiple users. Very dangerous.
2. Reflected -
The malicious script is reflected back immediately in the HTTP response. It's not stored anywhere on the server.
Example:
A link like: https://vulnerable.site/search?q=<script>alert('XSS')</script>
If the server blindly reflects back q in the HTML page, the script will run in the user’s browser when they click that link.
Impact:
Works well in phishing attacks. Affects one user at a time.
3. DOM -
The vulnerability lies entirely in the JavaScript code running in the browser — not on the server. Malicious input changes the DOM (Document Object Model) directly via JavaScript.Server may not log or even see this request. It's all on the client-side.


# How can XSS be exploited?
An attacker can:
Steal session cookies and hijack accounts.
Perform actions on behalf of a user.
Deface the website UI.
Redirect users to malicious websites.


# If <script> and alert() are Blocked, You Can Still Bypass!
XSS isn’t about the tag — it’s about executing JavaScript.
1.Use HTML Elements with Event Handlers
Leverage tags like <img>, <svg>, <iframe>, <video>, <object>.
Common event handlers: onerror, onload, onmouseover, onclick, etc.
2. If alert() is filtered, I use confirm(), prompt(), or console.log() to test execution.
3. Use payloads triggered by user actions like onmouseover.


# How do you prevent XSS in web applications?
Input Validation: Whitelist input wherever possible.
Output Encoding: Encode data before rendering it in HTML, JavaScript, or URLs.
Use Security Headers: Like Content-Security-Policy (CSP).
Escape Data Properly: Depending on context (HTML, JS, URL).
Use frameworks that auto-escape output (e.g., React, Angular).


# Can you give a real-world example of XSS exploitation?
1. In 2014, eBay had a stored XSS flaw where attackers could inject scripts into product listings. Unsuspecting buyers who visited those listings could have their cookies stolen or be redirected to phishing sites.
2. MySpace “Samy” Worm (2005)Samy Kamkar injected self-replicating JavaScript into his MySpace profile, infecting over a million users in hours. Impact: MySpace temporarily shut down due to massive disruption.
3. Google Blogspot XSS (2015) XSS via comment section let attackers run JavaScript on Blogspot blogs. Impact: Site defacements and potential user data theft; Google patched it fast.


# How would you report an XSS finding to a client?
Title: Reflected XSS in search parameter
Severity: High
Description: User-supplied input in the search parameter is reflected without sanitization, allowing execution of malicious scripts.
Steps to Reproduce: Include PoC URL
Impact: Session hijacking, account compromise
Recommendation: Proper output encoding and input validation


# What is CSP and how does it help?
CSP (Content Security Policy) is a browser feature that helps mitigate XSS by restricting the sources from which scripts can be loaded. For example, it can block inline scripts or scripts from unknown domains.


# Some Terms :
1. Session Stealing - Steal cookies from autheticated sessions and gain login tokens allowing them to login as victims.
2. Keyloggers - Logs everything you type and send your keystrokes to their server.(like login credentials or banking info)

# How would you test a web application if it's using a WAF (Web Application Firewall)?
Use obfuscation
Use alternate tags
Encode payloads (URL, HTML, Base64).
WAFs don’t see client-side JS, so focus on that to bypass(for DOM-based XSS)



