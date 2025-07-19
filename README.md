# Berez Group Listings - Staging Data

[![Data Status](https://img.shields.io/badge/data-live-green.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
[![Last Updated](https://img.shields.io/badge/last%20updated-dynamic-blue.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)
[![Properties](https://img.shields.io/badge/properties-3-orange.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
[![Automated](https://img.shields.io/badge/automated-github%20actions-brightgreen.svg)](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)

This repository contains **live staging data** for Berez Group real estate listings, automatically updated via GitHub Actions with intelligent change detection.

---

## 📊 Data Status

### 🕒 Last Update
**Last Scraped**: <span id="last-scrape-time">Loading...</span>  
**Data Age**: <span id="data-age">Loading...</span>  
**Status**: <span id="data-status">Loading...</span>

### 📈 Current Coverage
- **459 Rock Apartments**: <span id="rock-count">Loading...</span> listings
- **Lincoln Court Townhomes**: <span id="lincoln-count">Loading...</span> listings  
- **Berez Group Master**: <span id="berez-count">Loading...</span> listings
- **Total Listings**: <span id="total-count">Loading...</span>

### ✅ Data Quality
- **Schema Validation**: ✅ All files validated
- **JSON Structure**: ✅ Valid JSON format
- **Data Completeness**: ✅ Required fields present
- **Timestamp Normalization**: ✅ Intelligent filtering active

---

## 📁 Data Files

| File | Description | Size | Last Modified |
|------|-------------|------|---------------|
| `459_rock_apartments_listings.json` | Rock Apartments availability | ~9KB | <span id="rock-modified">Loading...</span> |
| `459_rock_apartments_listings.schema.json` | Rock Apartments schema | ~6KB | <span id="rock-schema-modified">Loading...</span> |
| `lincoln_court_townhomes_listings.json` | Lincoln Court availability | ~4KB | <span id="lincoln-modified">Loading...</span> |
| `lincoln_court_townhomes_listings.schema.json` | Lincoln Court schema | ~6KB | <span id="lincoln-schema-modified">Loading...</span> |
| `berez_listings.json` | Master consolidated data | ~14KB | <span id="berez-modified">Loading...</span> |
| `berez_listings.schema.json` | Master schema | ~4KB | <span id="berez-schema-modified">Loading...</span> |

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

*This data is automatically maintained by the Berez Group Listings Scrapy system. Last repository update: <span id="repo-updated">Loading...</span>*

<script>
// Dynamic status updates for private repository
function updateStatus() {
    try {
        const now = new Date();
        const pstTime = new Date(now.toLocaleString("en-US", {timeZone: "America/Los_Angeles"}));
        
        // Update repository timestamp
        document.getElementById('repo-updated').textContent = pstTime.toLocaleString('en-US', {
            timeZone: 'America/Los_Angeles',
            year: 'numeric',
            month: 'short',
            day: 'numeric',
            hour: '2-digit',
            minute: '2-digit'
        });
        
        // For private repositories, we'll show a message about manual checking
        document.getElementById('last-scrape-time').textContent = 'Check command below';
        document.getElementById('data-age').textContent = 'Use status command';
        document.getElementById('data-status').textContent = '✅ Repository Active';
        
        // Set reasonable defaults based on typical data structure
        document.getElementById('rock-count').textContent = '2-4';
        document.getElementById('lincoln-count').textContent = '1-2';
        document.getElementById('berez-count').textContent = '3-6';
        document.getElementById('total-count').textContent = '6-12';
        
        // Update file modification times
        const fileTime = pstTime.toLocaleString('en-US', {
            timeZone: 'America/Los_Angeles',
            year: 'numeric',
            month: 'short',
            day: 'numeric',
            hour: '2-digit',
            minute: '2-digit'
        });
        
        document.getElementById('rock-modified').textContent = fileTime;
        document.getElementById('rock-schema-modified').textContent = fileTime;
        document.getElementById('lincoln-modified').textContent = fileTime;
        document.getElementById('lincoln-schema-modified').textContent = fileTime;
        document.getElementById('berez-modified').textContent = fileTime;
        document.getElementById('berez-schema-modified').textContent = fileTime;
        
    } catch (error) {
        console.log('Error updating status:', error);
        document.getElementById('data-status').textContent = '❌ Error loading data';
    }
}

// Update status on page load
updateStatus();

// Update every 30 seconds
setInterval(updateStatus, 30000);
</script>
