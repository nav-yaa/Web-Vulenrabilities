# Price Tempering
Price Tempering is a type of web vulnerability where an attacker manipulates the price of a product or service during a transaction, typically by tampering with client-side data

# How to Identify
1. Browse through E-commerce or Payment Flows
- Look for places where the price is submitted from client-side (e.g., shopping cart, hidden fields).
2. Intercept Requests using Burp Suite/ZAP
- Focus on parameters like price, amount, total, discount, etc.
3. Try Tampering
- Change the price to a lower amount and see if the change reflects on the final billing page.
4. Check API Calls
- Inspect if mobile/web apps send the price from the client or calculate it on the server.


# Mitigation
1. Never trust client-side data like price, discount, total.
2. Always recalculate the total amount on the server side using trusted product data from the backend
3. Use unique product IDs and fetch prices from the database during the transaction.
4. Implement server-side validation for business logic.

