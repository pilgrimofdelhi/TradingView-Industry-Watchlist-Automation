# TradingView Industry Watchlist Automation

Automate the creation of sector/industry watchlists in TradingView using Python and Selenium!  
This script will visit every industry/sector page, select all stocks, and save them to a new TradingView watchlist. 100% automated.

---

## Features

- Batch-create TradingView watchlists for all sectors/industries
- Fully automated—no manual clicking required
- Works with Brave or Chrome browsers
- Resilient: retries and debug screenshots for troubleshooting

---

## Installation

### 1. **Clone this Repository**

```bash
git clone https://github.com/pilgrimofdelhi/tradingview-industry-watchlist-automation.git
cd tradingview-industry-watchlist-automation
```
### 2. Install Python & Selenium
Python 3.8+ required. 

[pip install selenium]

### 3. Download ChromeDriver
Download the correct ChromeDriver version for your Chrome/Brave browser.

Place chromedriver.exe in your project directory or somewhere on your system PATH.

### 4. Configure Paths
Edit these variables in your Python script to match your system:
```bash
[brave_path = r"C:\Program Files\BraveSoftware\Brave-Browser\Application\brave.exe"
chromedriver_path = r"D:\Python Bots\Bot\chromedriver.exe"
profile_path = r"D:\Python Bots\Mimic Bot\brave_selenium_profile"]
```
- brave_path: path to your brave.exe or chrome.exe
- chromedriver_path: path to your ChromeDriver executable
- profile_path: a folder path for a browser profile, so you stay logged in

### 5. Log In To TradingView in Your Profile
Start Brave/Chrome with your profile_path at least once and log in to TradingView manually. This ensures Selenium will use your logged-in session.

Example command (Windows):
```bash
["C:\Program Files\BraveSoftware\Brave-Browser\Application\brave.exe" --user-data-dir="D:\Python Bots\Mimic Bot\brave_selenium_profile"]
```
### 6. Run the Script
python watchlist_automation.py

## How it Works
1. Loads each TradingView sector/industry page from a preset list.

2. Waits for the stock table, then selects all stocks (skips headers).

3. Opens context menu, chooses "Add selected to Watchlist", then "Create new list".

4. Names the list after the URL segment (e.g., major-banks) and saves.

5. Takes debug screenshots for any errors.

No manual clicking required!

## Customizing
- Change the browser: Replace brave.exe path with chrome.exe for Chrome.

- Change the list of industry URLs:
Paste your own URLs in the industry_urls = [...] section.
I’ve already included all the current links in the code. However, if you’d like to learn or extract links for another market — for example, US stocks — you can generate the URLs using my DevTools snippet. - https://github.com/pilgrimofdelhi/tradingview-industry-link-extractor

- Adjust wait times:
If you get errors from slow internet, increase time.sleep() values.

- Screenshots:
Debug screenshots are saved in your script directory as debug_X_pageload.png or error_X.png.

## Troubleshooting
- Timeouts or pages not loading?
-- Increase sleep durations.
-- Check if TradingView is rate-limiting (add pauses between requests).

- Not logged in?
Make sure your browser profile is logged in and not in incognito.

- Selectors not working?
TradingView UI changes sometimes; update CSS/XPath selectors in the script if needed.

- Script crashes after many URLs?
Split your run into smaller batches or restart the script midway.

## Credits
Selenium code and project scaffolding: Rajat Kumar Singh. [@tradingwick_](https://x.com/tradingwick_)
