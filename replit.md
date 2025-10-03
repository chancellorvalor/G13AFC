# G13 Bot Tools - Wikipedia Bot

## Overview

This is a 10-year-old Wikipedia bot originally written for Python 2, now modernized to work with Python 3 and modern pywikibot. The bot helps manage Wikipedia's G13 deletion process for Articles for Creation (AfC) submissions.

## What Was Fixed

The project was successfully migrated from Python 2 to Python 3:

1. **Modern Pywikibot**: Replaced the old Python 2 pywikibot framework with the modern Python 3 version (10.5.0)
2. **Database Module**: Created `db_handle.py` to provide MySQL database connectivity
3. **Dependencies**: Installed python-dateutil, mysqlclient, and modern pywikibot
4. **Code Updates**: Fixed Python 2/3 compatibility issues in the main bot files

## Project Structure

- `g13_nudge_bot.py` - Main bot for notifying users about G13 candidates
- `g13_nom_bot.py` - Bot for nominating pages for G13 deletion
- `g13_db_maintenance.py` - Database cleanup and maintenance
- `db_handle.py` - MySQL database connection module
- `user-config.py` - User configuration for bot credentials
- `g13.sql` - Database schema for G13 tracking

## How to Use

### 1. Configure Bot Credentials

Edit `user-config.py` to add your Wikipedia bot username:

```python
usernames['wikipedia']['en'] = 'YourBotUsername'
```

### 2. Configure Database (Optional)

The bot uses MySQL to track G13 candidates. Edit `db_handle.py` to configure:

```python
DB_HOST = 'localhost'
DB_USER = 'wikiuser'  
DB_PASS = 'your_password'
```

Create the database:
```bash
mysql DATABASE < g13.sql
```

### 3. Run the Bot

The bot accepts category names to process:

```bash
python g13_nudge_bot.py -from:CATEGORY_NAME
```

For example:
```bash
python g13_nudge_bot.py -from:AfC_submissions_by_date/February_2009
```

### 4. Other Bots

- **Nomination Bot**: `python g13_nom_bot.py`
- **Database Maintenance**: `python g13_db_maintenance.py`

## Current Status

✅ Bot successfully migrated to Python 3
✅ Modern pywikibot (10.5.0) integrated
✅ Dependencies installed
✅ Basic functionality working

⚠️ MySQL database not configured (optional for full functionality)
⚠️ Wikipedia bot credentials need to be configured in user-config.py

## Notes

- The original Python 2 code has been backed up with `.bak` and `_old` extensions
- Some advanced features may need additional testing with modern pywikibot APIs
- Database features require MySQL server setup
