
# 🎶 Chinook SQL Analysis

This project explores the Chinook database, a digital media store dataset, using SQL queries across multiple relational tables.

## 🗂️ Database Overview

The Chinook database contains tables for:
- Albums, Artists, Customers, Employees
- Genres, Media Types, Playlists, Playlist Tracks
- Invoices, Invoice Items, Tracks

## 📊 Analysis Queries

### 🌍 Query 1: Non-USA Customers
```sql
SELECT CustomerId, FirstName, LastName, Country
FROM chinook.customers
WHERE Country <> 'USA';
```

### 🇧🇷 Query 2: Customers from Brazil
```sql
SELECT *
FROM chinook.customers
WHERE Country = 'Brazil';
```

### 💳 Query 3: Invoices for Brazilian Customers
```sql
SELECT customers.FirstName, customers.LastName, invoices.InvoiceDate, invoices.BillingCountry
FROM chinook.customers
JOIN chinook.invoices ON customers.CustomerId = invoices.CustomerId
WHERE invoices.BillingCountry = 'Brazil';
```

### 👥 Query 4: Sales Support Agents
```sql
SELECT *
FROM chinook.employees
WHERE Title = 'Sales Support Agent';
```

### 🌎 Query 5: Unique Billing Countries
```sql
SELECT DISTINCT BillingCountry
FROM chinook.invoices;
```

### 🧾 Query 6: Invoices per Sales Agent
```sql
SELECT employees.LastName, employees.FirstName, invoices.InvoiceId
FROM chinook.employees
JOIN chinook.customers ON employees.EmployeeId = customers.SupportRepId
JOIN chinook.invoices ON customers.CustomerId = invoices.CustomerId
WHERE employees.Title = 'Sales Support Agent';
```

### 💼 Query 7: Invoices with Customer and Agent Info
```sql
SELECT customers.FirstName AS CustomerFirstName, customers.LastName AS CustomerLastName, customers.Country AS CustomerCountry,
employees.FirstName AS EmployeeFirstName, employees.LastName AS EmployeeLastName, invoices.InvoiceId, invoices.Total AS Invoice_Total
FROM chinook.employees
JOIN chinook.customers ON employees.EmployeeId = customers.SupportRepId
JOIN chinook.invoices ON customers.CustomerId = invoices.CustomerId
WHERE employees.Title = 'Sales Support Agent';
```

### 📅 Query 8: Invoice Count in 2009
```sql
SELECT COUNT(*) AS Invoice_Count
FROM chinook.invoices
WHERE InvoiceDate BETWEEN '2009-01-01 00:00:00' AND '2009-12-31 23:59:59';
```

### 💰 Query 9: Total Sales in 2009
```sql
SELECT SUM(Total) AS TotalSales
FROM chinook.invoices
WHERE InvoiceDate BETWEEN '2009-01-01 00:00:00' AND '2009-12-31 23:59:59';
```

### 🎵 Query 10: Purchased Tracks by Invoice Line
```sql
SELECT tracks.Name AS PurchasedTrackName, invoice_items.InvoiceLineId
FROM chinook.tracks
JOIN chinook.invoice_items ON tracks.TrackId = invoice_items.TrackId;
```

### 🎶 Query 11: Purchased Tracks with Artist Name
```sql
SELECT tracks.Name AS PurchasedTrackName, artists.Name AS ArtistName, invoice_items.InvoiceLineId
FROM chinook.tracks
JOIN chinook.invoice_items ON tracks.TrackId = invoice_items.TrackId
JOIN chinook.albums ON tracks.AlbumId = albums.AlbumId
JOIN chinook.artists ON albums.ArtistId = artists.ArtistId;
```

### 💿 Query 12: All Tracks with Album, Media Type, and Genre
```sql
SELECT tracks.Name AS TrackName, albums.Title AS AlbumTitle, media_types.Name AS MediaType, genres.Name AS Genre
FROM chinook.tracks
JOIN chinook.albums ON tracks.AlbumId = albums.AlbumId
JOIN chinook.genres ON tracks.GenreId = genres.GenreId
JOIN chinook.media_types ON tracks.MediaTypeId = media_types.MediaTypeId;
```

### 🏆 Query 13: Total Sales by Sales Support Agent
```sql
SELECT employees.FirstName AS EmployeeFirstName, employees.LastName AS EmployeeLastName, SUM(invoices.Total) AS Total_Sales
FROM chinook.employees
JOIN chinook.customers ON employees.EmployeeId = customers.SupportRepId
JOIN chinook.invoices ON customers.CustomerId = invoices.CustomerId
WHERE employees.Title = 'Sales Support Agent'
GROUP BY employees.FirstName, employees.LastName;
```

### 🥇 Query 14: Top Sales Agent in 2009
```sql
SELECT employees.FirstName AS EmployeeFirstName, employees.LastName AS EmployeeLastName, SUM(invoices.Total) AS Total_Sales
FROM chinook.employees
JOIN chinook.customers ON employees.EmployeeId = customers.SupportRepId
JOIN chinook.invoices ON customers.CustomerId = invoices.CustomerId
WHERE employees.Title = 'Sales Support Agent'
AND InvoiceDate BETWEEN '2009-01-01 00:00:00' AND '2009-12-31 23:59:59'
GROUP BY employees.FirstName, employees.LastName
ORDER BY Total_Sales DESC
LIMIT 1;
```

---

## ✅ Summary

This project showcases multi-table joins, aggregations, filtering, and grouping to analyze digital media store operations and sales performance.
