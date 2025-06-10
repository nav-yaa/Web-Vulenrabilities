# Broken Access Control 
Broken Access Control occurs when users are able to perform actions or access resources that they shouldn’t be allowed to, due to improper enforcement of permissions.


# Types of Broken Access Control
1. Vertical Privilege Escalation
   - A low-privileged user accesses admin-only features.
2. Horizontal Privilege Escalation
   - A user accesses another user’s data.
3. Insecure Direct Object Reference (IDOR)
   - Users can access objects (files, data) by modifying parameters.

# How to Detect Broken Access Control
1. Log in as a normal user, then try accessing admin URLs or APIs.
2. Modify  URL params, POST body
3. Try brute-forcing or guessing URL paths (/admin, /config, /debug).
4. Changing role=user to role=admin in a request body or cookie.(Parameter Tmepering)
5. Try using different methods like PUT/DELETE on user objects.


# How to Exploit Acess Control 
1. Modifying parameters in the url
2. Accessing the API with missing access control on post,put,delete methods
3. Manipulating JWTs or Cookies
4. Exploiting CORS Misconfigurations that allows API access from unauthorised/untrusted origins
5. Forced Browsing

# Mitigation 
1. Implement Proper Access Control Checks
2. Grant the minimum privileges necessary
3. Avoid exposing internal object IDs directly

