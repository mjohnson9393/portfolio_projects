# Twitch Streamer Analytics: Top 1,000 Channels Analysis

**Tools:** Google Sheets (COUNTIF, SUMPRODUCT, conditional formatting) & SQL (DB Browser for SQLite)
**Dataset:** [Top 1000 Twitch Streamers Data](https://www.kaggle.com/) — Kaggle

## Overview
This project analyzes the top 1,000 Twitch streamers by followers to explore content trends, audience concentration by language, and streamer performance. The goal was to practice spreadsheet formulas (COUNTIF, SUMPRODUCT), conditional formatting with skewed data, and validate findings using SQL.

## 1. Which games dominate the "Most Streamed Game" category?
Using COUNTIF, I found **257 of the top 1,000 streamers list "Just Chatting"** as their most-streamed game (nearly 26%), reflecting its dominance as a Twitch category beyond traditional gaming. **Grand Theft Auto V** followed with 74 streamers.

## 2. How do total followers compare across language groups for "Personality" type streamers?
Using SUMPRODUCT, I calculated combined followers by language: **English (407.9M)**, **Spanish (185.7M)**, and **Japanese (20.4M)**. The relatively low Japanese total may reflect regional platform preferences rather than lower creator activity.

## 3. Which streamers are genuine top performers by average viewership?
I applied conditional formatting to highlight the top 10% of streamers by average viewers per stream. Because the data was heavily right-skewed (average: ~19,595 vs. max: 481,615), a simple "above average" threshold flagged most of the dataset — I used PERCENTILE to calculate a meaningful cutoff (~42,996 viewers) instead.

## 4. SQL validation
To demonstrate SQL proficiency alongside spreadsheet analysis, I recreated two queries in SQLite:

```sql
SELECT COUNT(*) FROM streamers WHERE MOST_STREAMED_GAME = 'Just Chatting';
```

Result: 257 (matched COUNTIF)

```sql
SELECT SUM(TOTAL_FOLLOWERS) FROM streamers WHERE LANGUAGE = 'English' AND TYPE = 'personality';
```

Result: 407,869,322 (matched SUMPRODUCT, after resolving a case-sensitivity mismatch in the data)

## 5. Which language has the most streamers overall?
Using GROUP BY, English led with 401 streamers, followed by Russian (115) and Spanish (106). Notably, this ranking differs from the follower-total comparison in Question 2 — suggesting Spanish-speaking streamers may have larger average followings per channel rather than more channels overall.

## Key Takeaways
"Just Chatting" has become Twitch's dominant category regardless of game content. Audience size and streamer count don't always correlate across language groups — a reminder to look at multiple metrics before drawing conclusions. Conditional formatting on skewed data requires statistical judgment (percentile, not raw average) to be meaningful. All spreadsheet findings were independently validated in SQL, including catching and resolving a real data-quality issue (case sensitivity).
