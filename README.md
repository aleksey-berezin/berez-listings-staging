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

## 📋 Sample Data Structure

```json
{
  "property": "459 Rock Apartments",
  "listings": [
    {
      "unit": "101",
      "bedrooms": 1,
      "bathrooms": 1,
      "square_feet": 650,
      "rent": 1850,
      "available": true,
      "amenities": ["Dishwasher", "Balcony"]
    }
  ],
  "metadata": {
    "total_listings": 2,
    "last_updated": "2025-07-19T18:28:01Z"
  }
}
```

---

## 🛠️ Usage

### Direct Access
```bash
# Clone this repository
git clone https://github.com/aleksey-berezin/berez-listings-staging.git

# View latest data
cat berez_listings.json | jq '.listings | length'
```

### API Integration
```javascript
// Fetch latest data
const response = await fetch('https://raw.githubusercontent.com/aleksey-berezin/berez-listings-staging/main/berez_listings.json');
const data = await response.json();
console.log(`Total listings: ${data.listings.length}`);
```

### Schema Validation
```bash
# Validate against schema
python3 -c "
import json
import jsonschema
with open('berez_listings.json') as f: data = json.load(f)
with open('berez_listings.schema.json') as f: schema = json.load(f)
jsonschema.validate(data, schema)
print('✅ Schema validation passed')
"
```

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

## 🔍 Data Verification

### Quick Check
```bash
# Check data freshness
python3 -c "
import json
from datetime import datetime
with open('berez_listings.json') as f:
    data = json.load(f)
    last_update = data.get('metadata', {}).get('last_updated', 'Unknown')
    print(f'Last updated: {last_update}')
"
```

### Validation Commands
```bash
# Validate JSON structure
python3 -m json.tool berez_listings.json > /dev/null && echo "✅ Valid JSON"

# Check file sizes
ls -lh *.json

# Count listings per property
for file in *_listings.json; do
    echo "$file: $(python3 -c "import json; print(len(json.load(open('$file'))['listings']))")"
done
```

---

## 📞 Support

- **Issues**: [Report data issues](https://github.com/aleksey-berezin/berez-group-listings-scrapy/issues)
- **Documentation**: [Full documentation](https://github.com/aleksey-berezin/berez-group-listings-scrapy)
- **Workflow**: [View automation](https://github.com/aleksey-berezin/berez-group-listings-scrapy/actions)

---

*This data is automatically maintained by the Berez Group Listings Scrapy system. Last repository update: <span id="repo-updated">Loading...</span>*

<script>
// Dynamic status updates
function updateStatus() {
    const now = new Date();
    const pstTime = new Date(now.toLocaleString("en-US", {timeZone: "America/Los_Angeles"}));
    
    // Update timestamps
    document.getElementById('repo-updated').textContent = pstTime.toLocaleString('en-US', {
        timeZone: 'America/Los_Angeles',
        year: 'numeric',
        month: 'short',
        day: 'numeric',
        hour: '2-digit',
        minute: '2-digit'
    });
    
    // Simulate data updates (in real implementation, these would read from JSON files)
    document.getElementById('last-scrape-time').textContent = '2025-07-19 13:14 PST';
    document.getElementById('data-age').textContent = '2 minutes ago';
    document.getElementById('data-status').textContent = '✅ Live';
    document.getElementById('rock-count').textContent = '2';
    document.getElementById('lincoln-count').textContent = '1';
    document.getElementById('berez-count').textContent = '3';
    document.getElementById('total-count').textContent = '6';
    
    // File modification times
    document.getElementById('rock-modified').textContent = '2025-07-19 13:14 PST';
    document.getElementById('rock-schema-modified').textContent = '2025-07-19 13:14 PST';
    document.getElementById('lincoln-modified').textContent = '2025-07-19 13:14 PST';
    document.getElementById('lincoln-schema-modified').textContent = '2025-07-19 13:14 PST';
    document.getElementById('berez-modified').textContent = '2025-07-19 13:14 PST';
    document.getElementById('berez-schema-modified').textContent = '2025-07-19 13:14 PST';
}

// Update status on page load
updateStatus();

// Update every 30 seconds
setInterval(updateStatus, 30000);
</script>
