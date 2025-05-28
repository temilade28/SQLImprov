
# 🎵 Spotify SQL Analysis

This project explores Spotify track data using SQL to uncover trends in artist popularity and track features.

## 🧰 Dataset  
Sourced from Kaggle, the dataset includes track-level metadata such as danceability, energy, tempo, and popularity.

## 🗄️ Table Creation
```sql
CREATE TABLE BIT_DB.Spotifydata (
    id INTEGER PRIMARY KEY,
    artist_name VARCHAR NOT NULL,
    track_name VARCHAR NOT NULL,
    track_id VARCHAR NOT NULL,
    popularity INTEGER NOT NULL,
    danceability DECIMAL(4,3) NOT NULL,
    energy DECIMAL(4,3) NOT NULL,
    key INTEGER NOT NULL,
    loudness DECIMAL(5,3) NOT NULL,
    mode INTEGER NOT NULL,
    speechiness DECIMAL(5,4) NOT NULL,
    acousticness DECIMAL(6,5) NOT NULL,
    instrumentalness TEXT NOT NULL,
    liveness DECIMAL(5,4) NOT NULL,
    valence DECIMAL(4,3) NOT NULL,
    tempo DECIMAL(6,3) NOT NULL,
    duration_ms INTEGER NOT NULL,
    time_signature INTEGER NOT NULL
);
```

## 📊 Analysis Queries

### 🎧 Average Track Metrics by Artist
```sql
SELECT
    artist_name,
    track_name,
    AVG(popularity) AS avg_popularity,
    AVG(danceability) AS avg_danceability,
    AVG(energy) AS avg_energy
FROM BIT_DB.spotifydata
GROUP BY artist_name, track_name;
```

### 🌟 Top 10 Tracks by Popularity
```sql
SELECT track_name, artist_name, popularity
FROM BIT_DB.spotifydata
ORDER BY popularity DESC
LIMIT 10;
```

### 🏅 Identify 'Top Star' Artists (Avg Popularity ≥ 90)
```sql
WITH popularity_average_CTE AS (
    SELECT artist_name, AVG(popularity) AS average_popularity
    FROM Spotifydata
    GROUP BY artist_name
)
SELECT artist_name, average_popularity, 'Top Star' AS tag
FROM popularity_average_CTE
WHERE average_popularity >= 90;
```

---

This project demonstrates the use of grouping, aggregation, CTEs, and ranking to extract insights from music streaming data.
