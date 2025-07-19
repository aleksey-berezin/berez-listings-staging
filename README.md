# Berez Group Listings - Staging Data

[![Data Status](https://img.shields.io/badge/data-live-green.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
[![Last Updated](https://img.shields.io/badge/last%20updated-dynamic-blue.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)
[![Properties](https://img.shields.io/badge/properties-3-orange.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
[![Automated](https://img.shields.io/badge/automated-github%20actions-brightgreen.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)

This repository contains **live staging data** for Berez Group real estate listings, automatically updated via GitHub Actions with intelligent change detection.

---

## 📊 Data Status

### 🕒 Last Update
**Last Scraped**: 2025-07-19 21:49:05 UTC / 2025-07-19 13:49:05 PST (Duration: 4.4s)  
**Data Age**: Current  
**Status**: ✅ Operational

        ### 📈 Current Coverage
        **Total Listings**: 6 listings  
        **Properties**: Berez, Lincoln Court Townhomes, 459 Rock Apartments
        
        **Per Property**:
        - **Berez**: 3 listings
- **Lincoln Court Townhomes**: 1 listings
- **459 Rock Apartments**: 2 listings

### ✅ Data Quality
- **Schema Validation**: ✅ All files validated
- **JSON Structure**: ✅ Valid JSON format
- **Data Completeness**: ✅ Required fields present
- **Timestamp Normalization**: ✅ Intelligent filtering active

---

## 🔄 Update Process

### Automated Workflow
1. **Scraping**: Runs every 20 minutes via GitHub Actions
2. **Change Detection**: Compares normalized JSON (ignores timestamps)
3. **Upload**: Only uploads when real data changes detected
4. **Validation**: All files validated against schemas

### Intelligent Filtering
- ✅ **Excludes**: `scrape_date`, `timestamp`, `last_updated`
- ✅ **Focuses**: Actual listing data changes
- ✅ **Prevents**: Unnecessary uploads for timestamp-only changes

---

## 📊 Monitoring

### Source Repository
- **Main Scraper**: [berez-group-listings-scrapy](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
- **Workflow**: [Scrape and Upload](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)
- **Status**: [Real-time monitoring](https://github.com/aleksey-berezin/berez-group-listings-scrapy)

### Data Sources
- **459 Rock Apartments**: Real-time availability and pricing
- **Lincoln Court Townhomes**: Current listings and details
- **Berez Group Master**: Consolidated property data

---

## 📤 Upload Status

**Last Upload**: 2025-07-19 21:49:05 UTC / 2025-07-19 13:49:05 PST  
**Status**: ℹ️ No Recent Changes  
**Reason**: No changes - upload skipped

---

*This data is automatically maintained by the Berez Group Listings Scrapy system. Repository contains 6 total listings across 3 properties: Berez (3), Lincoln Court Townhomes (1), 459 Rock Apartments (2).*

*Last README update: 2025-07-19 21:49:06 UTC / 2025-07-19 13:49:06 PST*
