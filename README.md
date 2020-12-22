# LHPControl

LHPControl is a front-end Windows app for CryptoGnome's LickHunterPro bot. It is based on @Doojenever's variable pairs sccript and includes many new features. Sanduckchan  created charts based on the Binance Futures liquidations (http://www.lickhunter.com/data). The script fetches the pairs from the site and places them in the coins.json along with the current open orders. It adds logic for various static/white/blacklists, as well as ability to automatically stop new trading if certain thresholds are reached.

# Features:
- Pairs based on **Top 10 burned by Volume - 24h**, **Top 10 by Liq-Events - 24h**, **Average Liq-Volume in USD - 24h** and **Average Liq-Amount - 24h**.
- Set a maximum of traidingPairs
- Set a maximum of open orders to prevent too many being opened at a time.
- Open order isolation - When X percent of your wallet balance gets hit by open orders, only the open order pairs will be traded until the percentage drops below X.
- Restarts the processes every N minutes, as well as when a certain threshhold of memory usage is reached to mitigate the websocket leackage
- Displays logs and error logs
- Displays the IP and Country of the connection to let the user make sure they are not connecting from the US
- Displays the versions of the bot and LHPControl apps
- Displays user account info from Binance
- Displays cpu/memory utilization

**This release doesn't work for Bybit yet.**

# Prerequisites:
- PowerShell 5.1 - https://www.microsoft.com/en-us/download/details.aspx?id=54616
- You have to have the latest working LickHunterPro instance in place.

# Installation:
- Place **LHPC.exe** in the root of the LickHunterPro folder (Example: C:\LickHunterPro\).

## Variables:
- https://github.com/daisy613/LHPControl/wiki

# To run:
- Double-click on  **LHPC.exe**
