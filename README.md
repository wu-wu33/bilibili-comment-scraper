# Scrape-Bilibili-Comments

A Python script to scrape first-level and second-level comments from 
Bilibili videos for academic research.

## Overview

This tool collects user comments (both top-level and nested replies) from 
Bilibili videos using the official API. It handles pagination, rate 
limiting, and retry logic, and exports the results to a CSV file.

The script is designed for research purposes, such as sentiment analysis, 
discourse studies, and computational social science.

## Features

- Scrape first-level (L1) comments and second-level (L2) replies
- Automatic pagination using API cursors
- Rate limiting with random delays to avoid being blocked
- Retry mechanism for network failures
- Export to CSV with UTF-8 BOM (Excel-compatible)
- Includes user metadata: username, gender, level, likes, timestamp

## Requirements

```bash
pip install requests urllib3
