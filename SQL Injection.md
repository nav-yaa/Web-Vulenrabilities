## SQL Injection 
SQL Injection (SQLi) is a vulnerability that occurs when untrusted user input is inserted directly into an SQL query without proper validation or escaping, allowing attackers to interfere with the database.


Why is SQLi dangerous?
1. Can lead to unauthorized data access
2. Bypass login authentication
3. Delete or modify data


## How to detect SQL injection vulnerabilities
1. Identify User Input Points
   -Login forms
   -Search bars
   -Contact forms
   -URL parameters (?id=1)
   -Headers (User-Agent, Referer)
   -Cookies

2. Inject Simple Test Payloads and Check if:
   -Authentication is bypassed
   -SQL errors are thrown (e.g., syntax error, unclosed quote)
   -Delay in response (for time-based blind SQLi)
  
3. Use Tools for Detection
  -Burp Suite (Intruder / Scanner)
  -SQLMap (automated detection + exploitation)

4. Technique	What You Do	What You Observe
  -Boolean-based	Try: ' AND 1=1 -- vs ' AND 1=2 --	Page changes or stays same?
  -Time-based	' OR IF(1=1, SLEEP(5), 0) --	Does server delay?
  -Error-based	' or ' ORDER BY 100--	Do SQL errors show up?
  -Union-based	' UNION SELECT null, null --	Do results from another table appear?


## Types of SQL Injection 
1. In-Band SQLi
   - Error Based - Relies on verbose DB errors.
   - Union Based - Combines attacker query using UNION
2. Out-of-band SQLi - Used when no visible output and time delays don’t work. Triggers external interactions (DNS, HTTP)
3. Blind SQLi
   - Boolean Based -  Ask True/False questions.
   - Time Based - Infer data via delay.
4 Second order SQLi - The malicious input is stored in the database and executed later in a different context.


## Parameterized vs Non-Parameterized Queries
Data passed as separate argument in parameterized whereas in non-parameterized the Input is directly concatenated into query.


## Mitigation for SQL Injection
1. Use Parameterized Queries
2. Input Validation/ Proper Input Sanitization
3. Use Web Application Firewall (WAF)
4. Disable detailed SQL error messages
5. If parameterization isn't possible, escape special characters.
