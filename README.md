# LHPControl

![LHCP](https://i.ibb.co/kJPFwxz/LHPC-screens.png)

## Description

* LHPControl app adds a beautiful GUI and additional variable pair logic to @cryptognome's LickHunterPro bot.
* It is a front-end Windows app for CryptoGnome's LickHunterPro bot. It is based on @Doojenever's variable pairs script and includes many new features. Sanduckchan created charts based on the Binance Futures liquidations (http://www.lickhunter.com/data). The script fetches the pairs from the site and places them in the coins.json along with the current open orders. It adds logic for various static/white/blacklists, as well as ability to automatically stop new trading if certain thresholds are reached.
* It is a single drop and run executable.
* **NOTE: Bybit is not currently supported, but it's coming with the next release.**

## Features

* **Multiple bots:** Supports running multiple bots side by side! Just drop LHPC into the root of each bot and change the bot name in settings.
* **Dynamic liquidation stats analysis:** LHPC queries and analyses the current liquidation streams (from liquidationsniper.com) and updates the coins file with coins with most profitable liquidation statistics. Four different types of liquidation stats are available to chose.
* **Trading Modes:** trade either with 1) a static list of coins you have manually created, 2) a custom whitelist and the liquidation stats analysis, or 3) a custom blacklist and the liquidation stats analysis, including the ability to restrict the coins based on their trading age.
* **New coins sync:** when new coins become available, they are automatically added to the list of available coins.
* **Account info:** Displays updated account info, current P&L, current open positions with individual P&L, cross/isolation info and leverage.
* **Current pairs:** displays the list of trading pairs selected by the algorithm (coins.json).
* **Isolation Percentage Mode:** Open Order Isolation Percentage mode allows you to specify the margin wallet percentage at which the bot should stop opening new orders and only manage the currently opened ones.
* **Maximum open orders:** you can specify the maximum number of open orders after which the bot will enter the aforementioned Isolation mode.
* **Log monitoring:** the current logs are displayed and separated into Output and Error logs for Profit and Websocket processes, similar to the PM2 Monitor dashboard, which can also be opened at a click of a button.
* **Settings backup:** backs up the settings.json file when settings change.
* **Upgrade checking:** LHPC checks for an available upgrade when it starts and allows you to download an upgrade.
* **DebugDump:** debug information can be generated for your issue submissions. No personal information like keys or secrets is generated.
* **Clear coin list:** the list of available coins is displayed with all the currently trading coins in black and disabled coins in gray. Click on the coin to customize its settings.
* **Bulk coin updates:** Update all coins at the same time with the same settings.
* **GeoIP:** Displays your geo IP information and warns you if your IP is US-based. You can use an IP webproxy to mask your IP. Get one [here](https://www.webshare.io/?referral_code=wn3nlqpeqog7).
* **Default settings:** if the bot root directory does not contain any settings files, creates them with default settings.
* **CPU/Memory stats:** displays the current processor and memory utilisation per each process.

### Coming features:

* Bybit trading.
* Automatically update coins from Cross to Isolated mode.
* Remove delisted coins.
* Download recent trading history.
* Display today's Profit&Loss stats.
* Dynamic lickValue and offsets per coin.
* Send email alerts to user when errors appear in error logs.
* Custom profiles.
* Remote access.
* Integrate P&L tracker.

## Installation

* Install the latest version of [LickHunterPro](https://github.com/CryptoGnome/LickHunterPRO/releases/latest) into **a new folder** (Example: C:\BOTS\LHP001\).
* [Download](https://github.com/daisy613/LHPControl/releases/latest) the latest LHPC.exe and place in the root of the LickHunterPro folder.
* Run LHPC.exe

## Usage

### Variables

**Bot Settings:** (for up to date information on the bot, go to [LickHunterPro wiki](http://www.lickhunter.com/wiki/))
  - **key, secret**: This is where you enter your API KEYS from your exchange of choice, make sure that you enable trading & enable futures if you are using binance.
  - **auto_qty**: Toggle this True/False to enable automatic position sizing based on your balance.
  - **percentbal**: Use a percentage value here to be used the auto_qty setting, this will tell the bot how much of your balance to use for each buy. Ths bot can be very aggressive on big moves so you want to make sure you account for a multitude of buys/sells to come through at any given time, we recommend using a value of less the 0.25 here, higher than that is considered VERY AGGRESSIVE if you would like to run more conservative lower this value.
  - **maxPosition**: This is the maximum position you want the bot to build in %, this is good to use if you want to prevent your bot from using your entire account on one position for risk management or if you run multiple bots on that account.
  - **longQty & shortQty**: If auto_qty is set to False, override value goes here. Otherwise ignore these settings - this is for the user who wants to set an exact qty of their buys and sells. This value is a percentage of your balance.
  - **VWAP offsets**: This is where you set the bot price offsets, based on percentage values away from LickHunters proprietary VWAP. The bot will only look to enter positions when price is ranging outside of these values & there is a liquidation on the traded coin.
  - **leverage**: Set this on exchange to ISOLATED then make it match below to help calculate order sizing. Suggested leverage for this bot is 3-5x, please note with higher leverage this bot becomes more risky.
  - **lickValue**: Set this to the size of liquidations you want to hunt for. This will always be a $USD value.
  - **takeProfit & stopLoss**: Take Profit & Stop Loss Values, these values are a percentage % and are based off your average entry price. Please Adjust to your risk levels. Take Profit is a LIMIT - REDUCE ONLY ORDER. STOP LOSS is a active MARKET ORDER that is not placed in the books. To disable set the Stop Loss amount at a high value.
  - **DCA**: Dollar Cost Averaging: This allows the bot to view the bots draw down when in an open position and adjust the buy qty in REALTIME when there is a liquidation. There are two things this looks at, one your current level, ex: levelOne = 2. This is a percent value, if your position is less than this it will use the autoQty value to make a buy/sell on liquidation. If it is past this value, lets say the position -2.5% away from your average entry it will then use multiplierOne value and multiple you autoQty value by this. So lets say your normal buy was 100 contracts, your multiplierOne = 2, your new buy value would be 200 contracts. So to recap, your level is % value away from your average entry in drawdown that it will activate a higher order size. Your multiplier is the value you multiple your original qty with.
  - **authentication**: For Binance Futures: use the Code 'ALPHA'. For Bybit: Go to your Bybit account and copy your UID, then Direct Message @CryptoGnome#7769 to be added to the auth server - you must use CryptoGnome's link to create the Bybit account!
  - **discordWebhook**: POST NOTIFICATIONS TO DISCORD CHANNEL, ENTER THE WEBHOOK ADDRESS FROM CHANNEL SETTINGS HERE. You mus make a new discord server for your self, make a channel, right click the channel and copy the webhook address to paste below.

**varPairs Settings:**
  - **botName**: name for your bot. [LHP001]
  - **maxOpen**: Maximum orders you want to have open at the same time. [3] 
  - **maxPairs**: Maximum pairs you want to trade, always the top of the chart is used [8]
  - **openOrderIsolationPercentage**: Only trade open order pairs when X percentage of wallet balance is reached. [10]
  - **tradingMode**: Choose a mode to base match your pairs. Modes: 1. staticPairs 2. whitelist 3. tradingAge. [1]
  - **staticPairs**: Trade only the pairs you want to trade.
  - **whitelist**: Set your personal whitelist of pairs you want to be able to trade.
  - **tradingAge**: All coins below trading age will not be traded. [14]
  - **blacklist**: You can blacklist coins that are that are higher than your trading age, so they won't be traded.
  - **tradePairs**: Choose 1, 2, 3 or 4, depending what chart your want to base your pairs on (1. Top 10 burned by Volume - 24h, 2. Top 10 by Liq-Events - 24h, 3. Average Liq-Volume in USD - 24h, 4. Average Liq-Amount - 24h). [1]
  - **fundingRateThreshold**: true or false, default is false, set to true if you don't want to trade pairs with a high Funding Rate. [false]
  - **maxFundingRate**: For explanation about funding rate you can read go [here](https://www.binance.com/en/support/faq/360033525031)
  - **tradingEnabled**: if unchecked, will not run WebSocket process.
  - **refreshTime**: interval at which the script will poll for new values for coins.json. Avoid setting it too low (default: 15).

## Troubleshooting

* Please submit issues [here](https://github.com/daisy613/LHPControl/issues).
* Please include your debugDump.txt file that you generated by clicking the debugDump button.

## Donations

BTC: 199egmtTkcLVRHb2b88XBbQpyzM3pyVQw3
