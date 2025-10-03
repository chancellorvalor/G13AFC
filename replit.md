# G13 Bot Tools - Wikipedia Bot

## Overview

This is a 10-year-old Wikipedia bot originally written for Python 2, now modernized to work with Python 3 and modern pywikibot. The bot helps manage Wikipedia's G13 deletion process for Articles for Creation (AfC) submissions.

## What Was Fixed

The project was successfully migrated from Python 2 to Python 3:

1. **Modern Pywikibot**: Replaced the old Python 2 pywikibot framework with the modern Python 3 version (10.5.0)
2. **Dependencies**: Installed python-dateutil and modern pywikibot
3. **Code Updates**: Fixed Python 2/3 compatibility issues in the main bot files
4. **Simplified Architecture**: Removed MySQL database dependencies for a cleaner setup

## Project Structure

- `g13_nudge_bot.py` - Main bot for notifying users about G13 candidates (Python 3 compatible)
- `g13_interested_notify.py` - Interested users notification script (disabled - requires database)
- `user-config.py` - User configuration for bot credentials
- `old_python2_code/` - Archive directory containing legacy Python 2 scripts

## How to Use

### 1. Configure Bot Credentials

Edit `user-config.py` to add your Wikipedia bot username:

```python
usernames['wikipedia']['en'] = 'YourBotUsername'
```

### 2. Run the Bot

The bot accepts category names to process:

```bash
python g13_nudge_bot.py -from:CATEGORY_NAME
```

For example:
```bash
python g13_nudge_bot.py -from:AfC_submissions_by_date/February_2009
```

### 3. Legacy Scripts

Legacy Python 2 scripts have been moved to `old_python2_code/` directory:
- `g13_nom_bot.py` - Nomination bot (requires database and Python 2 compatibility)
- `afc_cleaner.py` - AFC cleaner script (requires database and Python 2 compatibility)

## Current Status

✅ Bot successfully migrated to Python 3
✅ Modern pywikibot (10.5.0) integrated
✅ Dependencies installed
✅ Basic functionality working
✅ All deprecation warnings fixed
✅ Database dependencies removed for simplified setup

⚠️ Wikipedia bot credentials need to be configured in user-config.py

## Notes

- The original Python 2 code has been backed up to `old_python2/` directory
- Some advanced features may need additional testing with modern pywikibot APIs

## Features Disabled Without Database

The following features are **disabled** after database removal:
- **Notification tracking**: Bot cannot check if a user was already notified, so it may send duplicate notifications
- **Interested user notifications**: The g13_interested_notify.py script is non-functional
- **Database maintenance**: The g13_db_maintenance.py script has been removed

The core G13 notification functionality still works, but without tracking of previous notifications.
