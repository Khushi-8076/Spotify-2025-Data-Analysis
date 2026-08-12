# Spotify-2025-Data-Analysis
Spotify Data Analysis using Python | EDA | Data Visualization | Pandas | NumPy | Matplotlib | Seaborn

## 📌 Project Overview

This project analyzes Spotify's most streamed songs dataset using Python to understand streaming trends, artist popularity, song performance, collaboration impact, and relationships between different streaming metrics.

## The dataset contains **730 songs and 10 features**, including artist information, total Spotify streams, daily streams, daily stream rankings, collaboration status, and Spotify Wrapped rankings.

## ❗ Problem Statement

With thousands of songs competing for listener attention on Spotify, it is important to understand what factors are associated with a song's streaming success.

This project aims to analyze Spotify streaming data to answer questions such as:

* Which artists appear most frequently among the top-streamed songs?
* Which songs have the highest total Spotify streams?
* Which songs currently receive the highest daily streams?
* Is there a relationship between total streams and daily streams?
* Do collaboration songs perform better than solo songs?
* How are Spotify streams distributed across songs?
* Which streaming metrics are strongly correlated?
* Are there songs or artists that behave as outliers?
* Can streaming metrics help identify long-term versus current popularity?

---

## 🎯 Project Objectives

The main objectives of this project are:

1. Analyze the most-streamed Spotify songs of 2025.
2. Identify the most frequently appearing artists.
3. Compare total Spotify streams across songs.
4. Analyze daily streaming performance.
5. Compare solo songs and collaboration songs.
6. Study relationships between total streams and daily streams.
7. Identify outliers in streaming performance.
8. Analyze correlations between numerical variables.
9. Create meaningful features such as `Streams_per_artist` and `Popularity_Index`.
10. Generate visual insights using Matplotlib and Seaborn.

The notebook explicitly defines the objective as identifying streaming trends, artist popularity, collaboration impact, and relationships among streaming metrics.

---

## 📊 Dataset Information

### Dataset Size

* **Rows:** 730
* **Columns:** 10
* **Domain:** Music / Streaming Analytics

### Dataset Columns

| Column                      | Description                                   |
| --------------------------- | --------------------------------------------- |
| `rank`                      | Overall ranking of the song                   |
| `track`                     | Song/track name                               |
| `Artist`                    | Artist associated with the song               |
| `Billed_artist_count`       | Number of billed artists                      |
| `Collaboration`             | Indicates whether the song is a collaboration |
| `Spotify_streams_total`     | Total Spotify streams                         |
| `Daily_streams`             | Current daily streams                         |
| `Daily_streams_rank`        | Ranking based on daily streams                |
| `Daily_stream_share_pct`    | Share of daily streams                        |
| `Wrapped_global_top10_rank` | Spotify Wrapped global Top 10 ranking         |

The notebook's initial dataset output confirms these 10 fields.

---

# 🧹 Data Cleaning

The project performs the following data-cleaning activities:

### 1. Missing Value Detection

Missing values were checked using:

`df.isnull().sum()`

The `Wrapped_global_top10_rank` column initially contained **727 missing values**, while the remaining columns had no missing values.

### 2. Missing Value Treatment

Missing values in `Wrapped_global_top10_rank` were replaced with `0`.

This resulted in zero missing values across all columns.

### 3. Duplicate Records

Duplicate records were checked and removed using:

`df.drop_duplicates(inplace=True)`

The final duplicate check returned **0 duplicate records**.

### 4. Data Types

The dataset contains:

* Integer columns for rankings and stream counts
* Object columns for track and artist names
* Boolean column for collaboration
* Float columns for percentage/ranking-related fields

The notebook confirms the final data types after cleaning.

---

# 🔎 Exploratory Data Analysis

## Artist Distribution

The top 10 artists by number of songs in the dataset are:

| Artist            | Number of Songs |
| ----------------- | --------------: |
| Bad Bunny         |              15 |
| Sabrina Carpenter |              14 |
| Taylor Swift      |              12 |
| Tate McRae        |              10 |
| Neton Vega        |              10 |
| Olivia Dean       |               9 |
| Morgan Wallen     |               9 |
| Fuerza Regida     |               9 |
| Peso Pluma        |               8 |
| Victor Mendivil   |               7 |

Bad Bunny has the highest representation with **15 songs**, followed by Sabrina Carpenter with **14**.

---

# 📈 Visualization & Chart Details

## 1. Histogram — Distribution of Daily Streams

### Chart Type

**Histogram**

### Variables

* X-axis: `Daily_streams`
* Y-axis: Frequency

### Purpose

This chart shows how daily streams are distributed across the songs.

### Business/Analytical Question

**How frequently do different levels of daily streams occur among Spotify songs?**

### Insight

The distribution of daily streams is highly skewed. Most songs receive relatively lower daily streams, while a small number of songs receive exceptionally high daily streams.

This indicates that current listener engagement is concentrated among a small group of highly popular songs.

---

## 2. Histogram — Distribution of Total Spotify Streams

### Chart Type

**Histogram**

### Variables

* X-axis: `Spotify_streams_total`
* Y-axis: Frequency

### Purpose

To understand how cumulative Spotify streams are distributed among the songs.

### Business/Analytical Question

**Are total Spotify streams evenly distributed across songs?**

### Insight

Total Spotify streams are also highly unevenly distributed. A small number of songs have exceptionally high cumulative streams and behave as outliers.

## The dataset's total-stream maximum is approximately **1.95 billion streams**, compared with a mean of approximately **233.7 million**.

## 3. Scatter Plot — Total Streams vs Daily Streams

### Chart Type

**Scatter Plot**

### X-axis

`Spotify_streams_total`

### Y-axis

`Daily_streams`

### Hue

`Collaboration`

### Purpose

To determine whether songs with high cumulative streams also receive high current daily streams.

### Business/Analytical Question

**Does long-term popularity relate to current listener engagement?**

### Insight

There is a positive relationship between total Spotify streams and daily streams.

In general, songs with higher cumulative streams tend to have higher daily streams, although there are exceptions.

This helps distinguish:

* **Long-term popularity:** Total Spotify streams
* **Current popularity:** Daily streams

---

## 4. Bar Chart — Top 10 Artists by Total Spotify Streams

### Chart Type

**Bar Chart**

### X-axis

`Spotify_streams_total`

### Y-axis

`Artist`

### Purpose

To compare streaming performance among the top-ranked artists.

### Business/Analytical Question

**Which artists dominate Spotify streaming performance?**

### Insight

A relatively small number of artists dominate the top positions of the dataset.

Artist representation and streaming performance indicate that popular artists contribute significantly to Spotify's streaming activity.

---

## 5. Bar Chart — Top Songs by Total Spotify Streams

### Chart Type

**Bar Chart**

### X-axis

`Spotify_streams_total`

### Y-axis

`track`

### Purpose

To identify songs with the highest cumulative Spotify streams.

### Business/Analytical Question

**Which songs have achieved the strongest cumulative streaming performance?**

### Top Songs

Based on the dataset ranking, the leading songs include:

1. Ordinary — Alex Warren
2. DtMF — Bad Bunny
3. Golden — HUNTR/X
4. BAILE INoLVIDABLE — Bad Bunny
5. The Fate of Ophelia — Taylor Swift

The first song, **Ordinary**, has approximately **1.95 billion total streams** in the dataset.

---

## 6. Box Plot — Daily Streams Rank by Billed Artist Count

### Chart Type

**Box Plot**

### X-axis

`Billed_artist_count`

### Y-axis

`Daily_streams_rank`

### Purpose

To examine how daily streaming rankings vary according to the number of billed artists.

### Business/Analytical Question

**Does the number of billed artists affect daily streaming ranking?**

### Insight

The dataset contains primarily songs with one billed artist, while a smaller number have two.

The analysis suggests that having multiple artists can be associated with strong streaming performance in some cases, but collaboration alone does not guarantee a better daily-stream ranking.

---

## 7. Count Plot — Collaboration vs Solo Songs

### Chart Type

**Count Plot**

### X-axis

`Collaboration`

### Y-axis

Number of Songs

### Purpose

To compare the number of solo songs with collaboration songs.

### Business/Analytical Question

**Are most successful Spotify songs solo tracks or collaborations?**

### Insight

Most songs in the dataset are **solo tracks**, while collaboration songs represent a smaller proportion.

This indicates that collaboration is not a requirement for achieving high Spotify streaming performance.

---

## 8. Pie Chart — Collaboration vs Solo Songs

### Chart Type

**Pie Chart**

### Variable

`Collaboration`

### Purpose

To show the proportion of solo songs versus collaboration songs.

### Business/Analytical Question

**What percentage of the dataset consists of collaboration songs?**

### Insight

The pie chart provides a percentage-based view of the same relationship shown by the count plot.

The dataset is dominated by solo songs, with collaboration tracks making up a smaller share.

---

## 9. Heatmap — Correlation Matrix

### Chart Type

**Correlation Heatmap**

### Variables

* `rank`
* `Spotify_streams_total`
* `Daily_streams`
* `Daily_stream_share_pct`

### Purpose

To identify relationships between numerical variables.

### Business/Analytical Question

**Which Spotify metrics have the strongest relationships with each other?**

### Insight

The correlation analysis shows a positive relationship between:

`Spotify_streams_total` ↔ `Daily_streams`

This means songs with higher cumulative streams generally tend to have higher current daily streams.

Other numerical variables show comparatively weaker relationships.

---

## 10. Pair Plot — Numerical Variable Relationships

### Chart Type

**Pair Plot**

### Variables

* `Spotify_streams_total`
* `Daily_streams`
* `Daily_streams_rank`
* `Daily_stream_share_pct`

### Purpose

To visualize relationships and distributions among multiple numerical variables simultaneously.

### Business/Analytical Question

**How do different Spotify performance metrics interact with each other?**

### Insight

The pair plot provides a broader view of relationships among streaming metrics and helps identify patterns, clusters, and potential outliers.

---

# ⚙️ Feature Engineering

Two new features were created.

## 1. Streams per Artist

### Formula

`Streams_per_artist = Spotify_streams_total / Billed_artist_count`

### Purpose

To measure the average total streams attributable per billed artist.

### Why It Is Useful

This metric allows songs with different numbers of billed artists to be compared more fairly.

---

## 2. Popularity Index

### Formula

`Popularity_Index = Spotify_streams_total × Daily_stream_share_pct`

### Purpose

To create a combined metric incorporating cumulative streams and daily streaming share.

### Why It Is Useful

It can help identify songs that combine strong long-term streaming performance with strong current streaming contribution.

The notebook creates both features directly using these formulas.

---

# 📌 Key Findings

1. The dataset contains **730 songs and 10 features**.
2. A relatively small number of artists dominate Spotify streaming.
3. **Bad Bunny** has the highest number of appearances among the top 10 artists, with 15 songs.
4. Songs with higher total Spotify streams generally receive higher daily streams.
5. Most songs are solo tracks.
6. Collaboration tracks can achieve high streaming numbers, but collaboration does not automatically guarantee better daily rankings.
7. Daily-stream distribution is highly skewed.
8. Total Spotify streams and daily streams show a positive relationship.
9. The Top Songs and Top Artists charts highlight the strongest performers.
10. Artist popularity appears to have an important influence on total streaming performance.

---

# 🚨 Outlier Analysis

The project identifies several important outlier patterns:

### High Total Streams

A few songs have exceptionally high cumulative streams compared with the majority of the dataset.

### High Daily Streams

Some songs have exceptionally high current daily streams, indicating strong current listener engagement.

### Long-Term Popularity

Some songs have accumulated high total streams but currently have relatively lower daily streams.

### Viral/Current Popularity

Some songs show very high daily streams despite having comparatively lower cumulative streams.

### Artist Concentration

A small number of artists appear multiple times among the highest-streamed songs.

### Collaboration Outliers

Some collaboration songs achieve high streaming performance, but collaboration itself does not guarantee higher rankings.

These observations are consistent with the notebook's documented outlier analysis.

---

# 💡 Business/Analytical Insights

The project can be useful for understanding:

* Artist popularity
* Song performance
* Current listener engagement
* Long-term streaming success
* Collaboration effectiveness
* Streaming concentration
* Popularity patterns
* Outlier songs
* Relationship between current and cumulative streams

For a music-streaming platform, these insights could support content promotion, artist strategy, playlist placement, and trend identification.

---

# 🏁 Conclusion

This project analyzed Spotify's most-streamed songs using **Python, Pandas, NumPy, Matplotlib, and Seaborn**.

The analysis covered:

* Data loading
* Data overview
* Missing-value handling
* Duplicate detection
* Data-type analysis
* Exploratory Data Analysis
* Artist distribution
* Summary statistics
* Multiple visualizations
* Correlation analysis
* Pairwise analysis
* Feature engineering
* Outlier identification

The analysis indicates that artist popularity has an important influence on total streams. Daily streams provide an indication of current listener engagement, whereas total streams reflect accumulated long-term popularity.

Collaboration can improve visibility, but the analysis indicates that collaboration alone is not sufficient to guarantee higher streaming performance.

---

# 🚀 Future Scope

1. Build an interactive dashboard using **Power BI or Streamlit**.
2. Connect the **Spotify API** for real-time streaming analysis.
3. Develop a machine-learning model to predict future song popularity.
4. Perform genre-wise streaming analysis.
5. Perform country-wise streaming analysis.
6. Build a music recommendation system based on streaming behavior.

The notebook itself proposes these future enhancements.

---

# 🛠️ Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook

---

# 📂 Project Workflow

```text
Dataset
   ↓
Data Loading
   ↓
Data Overview
   ↓
Data Cleaning
   ├── Missing Values
   ├── Duplicate Records
   └── Data Types
   ↓
Exploratory Data Analysis
   ├── Artist Distribution
   └── Summary Statistics
   ↓
Data Visualization
   ├── Histogram
   ├── Scatter Plot
   ├── Bar Charts
   ├── Box Plot
   ├── Count Plot
   ├── Pie Chart
   ├── Heatmap
   └── Pair Plot
   ↓
Feature Engineering
   ├── Streams_per_artist
   └── Popularity_Index
   ↓
Key Findings
   ↓
Conclusion
```

---

# 👩‍💻 Skills Demonstrated

* Data Cleaning
* Exploratory Data Analysis
* Data Visualization
* Statistical Analysis
* Correlation Analysis
* Feature Engineering
* Python Programming
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Data Interpretation

---

## ⭐ Project Highlights

**Dataset:** 730 Spotify songs
**Features:** 10
**Domain:** Music Streaming Analytics
**Analysis:** EDA + Visualization + Feature Engineering
**Main Tools:** Python, Pandas, NumPy, Matplotlib, Seaborn
