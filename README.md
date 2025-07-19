# Berez Group Listings - Staging Data

[![Data Status](https://img.shields.io/badge/data-live-green.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
[![Last Updated](https://img.shields.io/badge/last%20updated-dynamic-blue.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)
[![Properties](https://img.shields.io/badge/properties-3-orange.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
[![Automated](https://img.shields.io/badge/automated-github%20actions-brightgreen.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)

This repository contains **live staging data** for Berez Group real estate listings, automatically updated via GitHub Actions with intelligent change detection.

---

## 📊 Data Status

### 🕒 Last Update
**Last Scraped**: Based on file timestamps  
**Data Age**: Current  
**Status**: ✅ Repository Active

### 📈 Current Coverage
- **459 Rock Apartments**: 2 listings
- **Lincoln Court Townhomes**: 1 listings  
- **Berez Group Master**: 3 listings
- **Total Listings**: 6 listings

### ✅ Data Quality
- **Schema Validation**: ✅ All files validated
- **JSON Structure**: ✅ Valid JSON format
- **Data Completeness**: ✅ Required fields present
- **Timestamp Normalization**: ✅ Intelligent filtering active

---

## 📁 Data Files

| File | Description | Size | Last Modified |
|------|-------------|------|---------------|
| `459_rock_apartments_listings.json` | Rock Apartments availability | ~9KB | Current |
| `459_rock_apartments_listings.schema.json` | Rock Apartments schema | ~6KB | Current |
| `lincoln_court_townhomes_listings.json` | Lincoln Court availability | ~4KB | Current |
| `lincoln_court_townhomes_listings.schema.json` | Lincoln Court schema | ~6KB | Current |
| `berez_listings.json` | Master consolidated data | ~14KB | Current |
| `berez_listings.schema.json` | Master schema | ~4KB | Current |

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

## 🔍 Quick Status Check

To see the current data status, run this command in the repository:

```bash
# Count listings in each file
for file in *_listings.json; do
    echo "$file: $(python3 -c "import json; print(len(json.load(open('$file'))['listings']))")"
done

# Check last update time
python3 -c "
import json
from datetime import datetime
with open('berez_listings.json') as f:
    data = json.load(f)
    last_update = data.get('metadata', {}).get('last_updated', 'Unknown')
    print(f'Last updated: {last_update}')
"
```

---

*This data is automatically maintained by the Berez Group Listings Scrapy system. Repository contains 6 total listings across 3 properties.*
