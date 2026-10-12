# Scrape-Bilibili-Comments

A Python script to scrape first-level and second-level comments from Bilibili videos for academic research.

## Overview

This tool collects user comments (both top-level and nested replies) from Bilibili videos using the official API. It handles pagination, rate limiting, and retry logic, and exports the results to a CSV file.

The script is designed for research purposes, such as sentiment analysis, discourse studies, and computational social science.

## Features

- Scrape first-level (L1) comments and second-level (L2) replies
- Automatic pagination using API cursors
- Rate limiting with random delays to avoid being blocked
- Retry mechanism for network failures
- Export to CSV with UTF-8 BOM (Excel-compatible)
- Includes user metadata: username, gender, level, likes, timestamp

## Requirements

    pip install requests urllib3

## Configuration

Before running, you need to fill in three variables at the top of the script:

    BVID    = "BVxxxxxxxxxx"
    HEADERS = {"User-Agent": "..."}
    COOKIES = {
        "SESSDATA": "...",
        "buvid3":   "...",
        "bili_jct": "...",
    }

### How to get cookies

1. Log in to Bilibili in your browser
2. Open Developer Tools (F12) → Application → Cookies
3. Copy SESSDATA, buvid3, and bili_jct

### How to get User-Agent

1. Open Developer Tools (F12) → Network
2. Refresh the page and click any request
3. Copy the User-Agent value from Request Headers

## Usage

    python scrape.py

The output will be saved as bilibili_comments2.csv.

## Output Format

| Column | Description |
|--------|-------------|
| 层级 | Level (L1 or L2) |
| root | Root comment ID (for L2 comments) |
| rpid | Comment ID |
| uname | Username |
| sex | Gender |
| level | User level |
| message | Comment text |
| like | Number of likes |
| ctime | Timestamp |

## How It Works

1. First-level comments: Uses the /x/v2/reply/main API endpoint, iterating through pages using the next cursor.
2. Second-level replies: For each first-level comment, uses the /x/v2/reply/reply API endpoint to fetch nested replies.
3. Rate limiting: Adds a random delay (1-2 seconds) between requests to avoid triggering Bilibili's anti-bot system.
4. Retry logic: Uses urllib3.Retry to handle transient network errors.

## Notes

- The script requires login cookies to access the API.
- Bilibili may rate-limit or block requests if the delay is too short.
- For large videos, scraping may take several hours.
- Cookies may expire after a few weeks; if the script stops working, refresh your cookies from the browser.
- Please respect Bilibili's terms of service and use this tool only for academic research.

## Disclaimer

This tool is intended for academic research purposes only. Users are responsible for complying with Bilibili's terms of service and applicable data protection laws.

## Contact

Yuanyuan Wu — florencewu103@gmail.com
