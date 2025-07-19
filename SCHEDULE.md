# Berez Listings Scraping Schedule

This document outlines the automated scraping schedule for Berez Group property listings.

## Schedule Overview

### **Monday - Saturday (Business Days)**
- **Active Hours**: 7:00 AM - 7:00 PM PDT
- **Frequency**: Every 15 minutes
- **Times**: 7:00, 7:15, 7:30, 7:45, 8:00, 8:15, 8:30, 8:45, 9:00, 9:15, 9:30, 9:45, 10:00, 10:15, 10:30, 10:45, 11:00, 11:15, 11:30, 11:45, 12:00, 12:15, 12:30, 12:45, 1:00, 1:15, 1:30, 1:45, 2:00, 2:15, 2:30, 2:45, 3:00, 3:15, 3:30, 3:45, 4:00, 4:15, 4:30, 4:45, 5:00, 5:15, 5:30, 5:45, 6:00, 6:15, 6:30, 6:45, 7:00 PM

### **Sunday (Reduced Schedule)**
- **Frequency**: 4 times per day
- **Times**: 
  - **6:00 AM PDT** / 13:00 UTC
  - **12:00 PM PDT** / 19:00 UTC  
  - **6:00 PM PDT** / 01:00 UTC (next day)
  - **12:00 AM PDT** / 07:00 UTC

### **After Hours (Monday-Saturday)**
- **Frequency**: Every 3 hours
- **Times**:
  - **9:00 PM PDT** / 04:00 UTC (next day)
  - **12:00 AM PDT** / 07:00 UTC
  - **3:00 AM PDT** / 10:00 UTC
  - **6:00 AM PDT** / 13:00 UTC

## Time Zone Information

All times are displayed in both **UTC** and **PDT** (Pacific Daylight Time) with **PDT in bold** for easier reading.

### **PDT vs UTC Conversion**
- **PDT** = UTC - 7 hours (during Daylight Saving Time)
- **PST** = UTC - 8 hours (during Standard Time)

## Schedule Details

### **Business Hours (Monday-Saturday)**
- **Start**: **7:00 AM PDT** / 14:00 UTC
- **End**: **7:00 PM PDT** / 02:00 UTC (next day)
- **Total Runs**: 48 times per day (every 15 minutes for 12 hours)

### **Sunday Schedule**
- **Reduced frequency** for weekend maintenance
- **4 runs per day** at strategic times
- **Covers morning, afternoon, evening, and overnight**

### **After Hours Coverage**
- **Continuous monitoring** outside business hours
- **Every 3 hours** ensures data freshness
- **Covers overnight and early morning periods**

## Technical Implementation

### **GitHub Actions Cron Expressions**
```yaml
# Monday-Saturday: 7am-7pm every 15 minutes
- cron: '0,15,30,45 7-18 * * 1-6'

# Sunday: 4 times per day (6am, 12pm, 6pm, 12am)
- cron: '0 6,12,18,0 * * 0'

# After hours: Every 3 hours (9pm, 12am, 3am, 6am)
- cron: '0 21,0,3,6 * * 1-6'
```

### **Total Daily Runs**
- **Monday-Saturday**: 52 runs per day (48 business hours + 4 after hours)
- **Sunday**: 4 runs per day
- **Weekly Total**: 320 runs per week

## Monitoring and Alerts

- **Success notifications** sent to repository
- **Failure alerts** trigger immediate investigation
- **README updates** show last successful scrape time
- **Upload metrics** track data changes and upload reasons

---

*This schedule ensures comprehensive coverage of property listings with appropriate frequency for business needs while maintaining system efficiency.* 