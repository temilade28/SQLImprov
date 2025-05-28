
# 🎬 Netflix SQL Analysis

This project explores Netflix TV and movie content using SQL, based on datasets sourced from Kaggle.

## 🗄️ Dataset Tables

- **netflix_titles_info**: Contains title, type, country, date added, rating, duration, genres.
- **netflix_people**: Contains show IDs, directors, and cast information.

## 🏗️ Table Creation
```sql
CREATE TABLE netflix_titles_info (
    show_id VARCHAR(5), type VARCHAR(7), title VARCHAR(58), country VARCHAR(74),
    date_added TIMESTAMP, release_year INT, rating VARCHAR(5), duration VARCHAR(9), listed_in VARCHAR(74)
);
CREATE TABLE netflix_people (
    show_id VARCHAR(5), director VARCHAR(54), cast VARCHAR(532)
);
```
(Data inserted from provided Netflix CSV samples.)

## 📊 Analysis Queries

### 🎞️ Query 1: Count of Movies
```sql
SELECT COUNT(type)
FROM netflix_titles_info
WHERE type = 'Movie';
```
**Result**: Total number of movies in the database.

---

### 🕒 Query 2: Most Recent Addition
```sql
SELECT MAX(date_added)
FROM netflix_titles_info;
```
**Result**: Date when the latest movie or TV show was added.

---

### 🔤 Query 3: Alphabetical List of Titles
```sql
SELECT title
FROM netflix_titles_info
ORDER BY title ASC;
```
**Result**: All movies and TV shows sorted A–Z.

---

### 🎬 Query 4: Director of 'The Starling'
```sql
SELECT people.director
FROM netflix_people people
LEFT JOIN netflix_titles_info titles ON people.show_id = titles.show_id
WHERE titles.title = 'The Starling';
```
**Result**: Name of the director for *The Starling*.

---

### 📽️ Query 5: Oldest Movie in the Database
```sql
SELECT release_year, title
FROM netflix_titles_info
WHERE type = 'Movie'
ORDER BY release_year ASC
LIMIT 1;
```
**Result**: Title and release year of the oldest movie.

---

## ✅ Summary

This project demonstrates querying across multiple tables, using joins, filtering, sorting, and aggregation to uncover insights into Netflix’s catalog.

