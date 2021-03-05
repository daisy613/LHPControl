# LHPControl

![LHCP](https://i.imgur.com/Jt4mwWC.png)

## Description

* LHPControl app adds a beautiful GUI and additional variable pair logic to @cryptognome's LickHunterPro bot.
* It is a front-end Windows app for CryptoGnome's LickHunterPro bot. It is based on @Doojenever's variable pairs script and includes many new features. Sanduckchan created charts based on the Binance Futures liquidations (http://www.lickhunter.com/data). The script fetches the pairs from the site and places them in the coins.json along with the current open orders. It adds logic for various static/white/blacklists, as well as ability to automatically stop new trading if certain thresholds are reached.
* It is a single drop and run executable.

## Features

* **Multiple bots:** Supports running multiple bots side by side! Just drop LHPC into the root of each bot and change the bot name in settings.
* **Dynamic liquidation stats analysis:** LHPC queries and analyses the current liquidation streams (from liquidationsniper.com) and updates the coins file with coins with most profitable liquidation statistics. Four different types of liquidation stats are available to chose.
* **Trading Modes:** trade either with 1) a static list of coins you have manually created, 2) a custom whitelist and the liquidation stats analysis, or 3) a custom blacklist and the liquidation stats analysis, including the ability to restrict the coins based on their trading age.
* **New coins sync:** when new coins become available, they are automatically added to the list of available coins.
* **Account info:** Displays updated account info, current P&L, current open positions with individual P&L, cross/isolation info and leverage.
* **Current pairs:** displays the list of trading pairs selected by the algorithm (coins.json).
* **Isolation Percentage Mode:** Open Order Isolation Percentage mode allows you to specify the margin wallet percentage at which the bot should stop opening new orders and only manage the currently opened ones.
* **Maximum open orders:** you can specify the maximum number of open orders after which the bot will enter the aforementioned Isolation mode.
* **Automatic Trading Mode**: LHPC sets all pairs to Isolated trading mode on Binance automaatically!
* **Delisted coin removal**: delisted coins are automatically removed.
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

* Download recent trading history.
* Dynamic lickValue and offsets per coin.
* Send email alerts to user when errors appear in error logs.
* Custom profiles.
* Remote access.
* Integrate P&L tracker.

## Installation instructions:

[Click here for instructions wiki](https://github.com/daisy613/LHPControl/wiki)

## Donations

* USDT/ETH (ERC20): 0x56b2239c6bde5dc1d155b98867e839ac502f01ad
* USDT (TRC20): TNuwZebdZmoDxrJRxUbyqzG48H4KRDR7wB (if sending from Binance account - allows for less fees)
* BTC: 1PV97ppRdWeXw4TBXddAMNmwnknU1m37t5
