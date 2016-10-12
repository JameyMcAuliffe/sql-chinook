1)Provide a query showing Customers (just their full names, customer ID and country) who are not in the US.

SELECT FirstName || " " || LastName AS "Name", CustomerId, Country FROM Customer
WHERE Country <> "USA"

