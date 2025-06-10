# XSS -  Cross Site Scripting 
Cross-Site Scripting (XSS) is a vulnerability that allows attackers to inject malicious scripts into web pages viewed by other users. These scripts usually run in the victim’s browser and can steal cookies, session tokens, or other sensitive information.


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
A link like:https://vulnerable.site/search?q=<script>alert('XSS')</script>
If the server blindly reflects back q in the HTML page, the script will run in the user’s browser when they click that link.
Impact:
Works well in phishing attacks. Affects one user at a time.

3. DOM -
The vulnerability lies entirely in the JavaScript code running in the browser — not on the server. Malicious input changes the DOM (Document Object Model) directly via JavaScript.Server may not log or even see this request. It's all on the client-side.


#






Some Terms :
1. 
