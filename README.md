# Google Stock Screener
*Have you ever wished a good selection of stocks be delivered daily to your inbox?* *Have you ever wished you could navigate in a few moments through the thousands of names available for investment in the stock markets?* **So did I.** 

Therefore, I created this module to support my own investment activity. 

What it does:
- It connects to the [Google Stock Screener API](https://www.google.com/finance/stockscreener);
- Runs a query on it based on certain fundamental stock screening criteria (e.g. [P/E ratio](http://wwww.investopedia.com/terms/p/price-earningsratio.asp), [Dividend Yield](http://wwww.investopedia.com/terms/d/dividendyield.asp), [EBITDA Margin](http://wwww.investopedia.com/terms/e/ebitda-margin.asp)).
- Delivers the result in a nice formatting to my inbox.

The module support **multi-exchange queries**, and a **maximum of 8 criteria** at a time.

## Installation Instructions
Tested with, and assumes you already have at your disposal:
- Ubuntu 16.04;
- Anaconda Python 3.5.3 
- Gmail email server. 

Install git
```
sudo apt-get update
sudo apt-get install git
```

Copy the repository on your computer and rename the sample config file
```
git clone https://github.com/terzim/GoogleStockScreener.git
cd GoogleStockScreener
mv config-sample.ini config.ini
```
Install the python requirements
```
conda install --yes --file requirements.txt  # If using Anaconda Python distribution
```
or
```
pip3 install -r requirements.txt # If using a standard Python3 distributions
```

## Configuration
Open the ```config.ini``` file in your favourite text editor. Edit the configuration parameters accordingly.

### Screener data

Sample config file:
```
[screener_data]
csv_file = YOUR_CSV_FILE_NAME (e.g. csv_file.csv)
json_file = YOUR_JSON_FILE_NAME (e.g. json_file.json)
currency = YOUR_CURRENCY_OF_CHOICE (e.g. USD)
; Note - if left empty, defaults to standard currency of exchange
exchanges = YOUR, LIST, OF, EXCHANGES, SEPARATED, BY COMMAS (e.g. NYSE, LON, BIT)
sector = YOUR_SECTOR_OF_CHOICE ** TODO **
; Note - to do leave sector empty for now
```

### Email Data
```
[email_data]
send_email = TRUE/FALSE
; set send_email to True is wish to send the email
sender = YOUR_SENDER_USERNAME (e.g. john@doe.com)
recipient = YOUR_RECIPIENT_EMAIL (e.g. recipient@example.com)
pwd_sender = YOUR_SENDER_PASSWORD (e.g. catdog123)
server_name = YOUR_SMTP_SERVER_NAME (e.g. smtp.gmail.com)
; Note - gmail server_name is smtp.gmail.com
server_port = YOUR_SMTP_SERVER_PORT (e.g. 587)
; Note - gmail server_post is 587
```

### Screening Criteria

These are also set at the bottom of the configuration file. A full list of the criteria (organized by topic) is to be found in the class documentation. **Leave blank the criteria you do not use**

```
[screening_criteria]
CRITERIA1 = (e.g. pe_ratio)
CRITERIA1_MIN = (e.g. 5)
CRITERIA1_MAX = (e.g. 15)
CRITERIA2 = (e.g. price_to_book)
CRITERIA2_MIN = 1
CRITERIA2_MAX = 3
CRITERIA3 =
CRITERIA3_MIN =
CRITERIA3_MAX =
CRITERIA4 =
CRITERIA4_MIN =
CRITERIA4_MAX =
CRITERIA5 =
CRITERIA5_MIN =
CRITERIA5_MAX =
CRITERIA6 =
CRITERIA6_MIN =
CRITERIA6_MAX =
CRITERIA7 =
CRITERIA7_MIN =
CRITERIA7_MAX =
CRITERIA8 =
CRITERIA8_MIN =
CRITERIA8_MAX =
```
### Run the screen
The screen can be run one-off
```
python StockScreener.py
```
or - in alternative - scheduled for periodical execution via crontab (and - possibly - a VPS). For instructions to setup crontab on a VPS, read a [shorthand guide here](https://www.digitalocean.com/community/tutorials/how-to-use-cron-to-automate-tasks-on-a-vps). 