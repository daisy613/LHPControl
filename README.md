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

# Variables:
  - key = 
  .... (insert stuff from Gnome's wiki)
  - $botName = the name for your bot **Example: LHP001**
  - $maxPositions = "3" **The maximum orders you want to have open at the same time**
  - $maxPairs = "8" **The maximum pairs you want to trade, always the top of the chart is used**
  - $openOrderIsolationPercentage = "10" **Only trade open order pairs when X percentage of wallet balance is reached**
  - $tadingMode = **Choose a mode to base match your pairs. Modes: 1. $staticPairs 2. $whitelist 3. $tradingAge**
  - $staticPairs = **Trade only the pairs you want to trade**
  - $whitelist = **Set your personal whitelist of pairs you want to be able to trade**
  - $tradingAge = **All coins below trading age will not be traded**
  - $blacklist = **You can blacklist coins that are above your trading age, so they won't be traded**
  - $tradePairs = "1" **Choose 1, 2, 3 or 4, depending what chart your wan't to base your pairs on (1. Top 10 burned by Volume - 24h, 2. Top 10 by Liq-Events - 24h, 3. Average Liq-Volume in USD - 24h, 4. Average Liq-Amount - 24h)**
  - $fundingRateThreshold = **$true or $false, default is $false, set to $true if you don't want to trade pairs with a high Funding Rate**
  - $maxFundingRate = **For explanation about funding rate you can read this https://www.binance.com/en/support/faq/360033525031**  
  - $tradingEnabled = if unchecked, will not run WebSocket process.
  - $refreshTime = the interval for script getting new values for coins.json (default: 5)

# Coin variables:
  - $longOffset = "2.7" **explanation**
  - $shortOffset = "2.7" **explanation**
  - $lickValue = "1000" **explanation**


# To run:
- Double-click on  **LHPC.exe**
