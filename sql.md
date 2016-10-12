1) Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.

SELECT FirstName || " " || LastName AS "Name", CustomerId, Country FROM Customer
WHERE Country <> "USA";

2) Provide a query only showing the Customers from Brazil.

SELECT * FROM Customer
WHERE Country = "Brazil";

3) Provide a query showing the Invoices of customers who are from Brazil. The resultant table should show the customer's full name, Invoice ID, Date of the invoice and billing country.

SELECT Customer.FirstName || " " || Customer.LastName AS "Name", InvoiceId, InvoiceDate, BillingCountry FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
WHERE Customer.Country = "Brazil";

4) Provide a query showing only the Employees who are Sales Agents.

SELECT * FROM Employee
WHERE Title LIKE "%Agent%";

5) Provide a query showing a unique list of billing countries from the Invoice table.

SELECT BillingCountry FROM Invoice
GROUP BY BillingCountry;
