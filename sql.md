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

6) Provide a query showing the invoices of customers who are from Brazil.

SELECT * FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
WHERE Customer.Country = "Brazil";

7) Provide a query that shows the invoices associated with each sales agent. The resultant table should include the Sales Agent's full name.

SELECT Employee.FirstName || " " || Employee.LastName AS "Sales Agent", Invoice.* FROM Invoice
JOIN Customer ON Invoice.CustomerId = Customer.CustomerId
JOIN Employee ON Customer.SupportRepId = EmployeeId
WHERE Employee.Title LIKE "%Agent%";

8) Provide a query that shows the Invoice Total, Customer name, Country and Sale Agent name for all invoices and customers.

SELECT Employee.FirstName || " " || Employee.LastName AS "Sales Agent", Invoice.Total, Customer.FirstName || " " || Customer.LastName AS "Customer Name", Customer.Country FROM Employee
JOIN Customer ON Employee.EmployeeId = Customer.SupportRepId
JOIN Invoice ON Customer.CustomerId = Invoice.CustomerId;

9) How many Invoices were there in 2009 and 2011? What are the respective total sales for each of those years?

SELECT Count(*) AS "Total Invoices 2009/2011" FROM Invoice
WHERE Invoice.InvoiceDate LIKE "2009%" OR Invoice.InvoiceDate LIKE "2011%";

SELECT SUM(Invoice.Total) AS "2009 Total Sales" FROM Invoice
Where Invoice.InvoiceDate LIKE "2009%";

SELECT SUM(Invoice.Total) AS "2011 Total Sales" FROM Invoice
Where Invoice.InvoiceDate LIKE "2011%";

10) Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for Invoice ID 37.

SELECT Count(*) FROM InvoiceLine
WHERE InvoiceId = "37";

11) Looking at the InvoiceLine table, provide a query that COUNTs the number of line items for each Invoice. HINT: GROUP BY

SELECT Count(*) FROM InvoiceLine
GROUP BY InvoiceLine.InvoiceId;

12) Provide a query that includes the track name with each invoice line item.

SELECT InvoiceLine.*, Track.Name FROM InvoiceLine
JOIN Track ON InvoiceLine.TrackId = Track.TrackId;

13) Provide a query that includes the purchased track name AND artist name with each invoice line item.

SELECT InvoiceLine.*, Track.Name, Artist.Name FROM InvoiceLine
JOIN Track ON InvoiceLine.TrackId = Track.TrackId
JOIN Album ON Track.AlbumId = Album.AlbumId
JOIN Artist ON Album.ArtistId = Artist.ArtistId;

14) Provide a query that shows the # of invoices per country. HINT: GROUP BY

SELECT BillingCountry, Count(*) FROM Invoice
GROUP BY BillingCountry;

15) Provide a query that shows the total number of tracks in each playlist. The Playlist name should be include on the resultant table.

SELECT Playlist.Name, Count(*) FROM Playlist
JOIN PlaylistTrack ON Playlist.PlaylistId = PlaylistTrack.PlaylistId
GROUP BY PlaylistTrack.PlaylistId;

16) Provide a query that shows all the Tracks, but displays no IDs. The resultant table should include the Album name, Media type and Genre.

SELECT Track.Name, Album.Title, MediaType.Name, Genre.Name FROM Track
JOIN Album ON Track.AlbumId = Album.AlbumId
JOIN MediaType ON Track.MediaTypeId = MediaType.MediaTypeId
JOIN Genre ON Track.GenreId = Genre.GenreId;

17) Provide a query that shows all Invoices but includes the # of invoice line items.

SELECT * FROM Invoice;
SELECT Count(*) FROM InvoiceLine;







