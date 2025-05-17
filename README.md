pip install MetaTrader5

---

import MetaTrader5 as metatrader
from datetime import datetime

---

metatrader.initialize()

---

login = 5036191085
password = '!tSqQn7l'
server = 'MetaQuotes-Demo'

---

metatrader.login(login, password, server)

---

rates = metatrader.copy_rates_from('EURUSD',metatrader.TIMEFRAME_D1,datetime.now(),100)
print(rates)

---

ticker = 'EURUSD'
interval = metatrader.TIMEFRAME_D1
from_date = datetime.now()
no_of_rows = 100

---

rates2 = metatrader.copy_rates_from(ticker,interval,from_date,no_of_rows)
print(rates2)

---

account_info = metatrader.account_info()
print(account_info)

---

account_info.balance

---

account_info.login

---

num_symbols = metatrader.symbols_total()
num_symbols

---

symbol_info = metatrader.symbols_get()
symbol_info

---

metatrader.symbol_info('EURUSD')

---

!pip install pandas

---

import pandas as pd

---

ohlc = pd.DataFrame(metatrader.copy_rates_range('EURUSD',metatrader.TIMEFRAME_D1, datetime(2023,12,21), datetime.now()))
ohlc

---

ohlc['time'] = pd.to_datetime(ohlc['time'],unit='s')
ohlc

---

!pip install plotly

---

import plotly.express as px

fig = px.line(
    ohlc,
    x='time',
    y='close',
    title='Évolution du prix de clôture',
    labels={'time': 'Date', 'close': 'Prix de clôture'}
)

fig.show(renderer='notebook')