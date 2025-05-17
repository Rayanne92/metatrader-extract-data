pip install MetaTrader5

import MetaTrader5 as metatrader
from datetime import datetime

metatrader.initialize()

login = 5036191085
password = '!tSqQn7l'
server = 'MetaQuotes-Demo'

metatrader.login(login, password, server)

rates = metatrader.copy_rates_from('EURUSD',metatrader.TIMEFRAME_D1,datetime.now(),100)
print(rates)

ticker = 'EURUSD'
interval = metatrader.TIMEFRAME_D1
from_date = datetime.now()
no_of_rows = 100

rates2 = metatrader.copy_rates_from(ticker,interval,from_date,no_of_rows)
print(rates2)

account_info = metatrader.account_info()
print(account_info)