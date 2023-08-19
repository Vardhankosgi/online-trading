# online-trading
online trading
import pandas as pd 
import numpy as np 
import tensorflow as tf
import matplotlib.pyplot as plt 
import pandas_datareader as data 
from keras.models import load_model 
import streamlit as st 
import altair as alt 
from altair import Chart
from datetime import datetime 
import yfinance as yf



st.title("stack trand prediction")
print("please enter the company name for knowing investers data")
user_input = st.text_input('Enter stock Ticker','AAPL')
df  = yf.download(user_input, start='2018-01-01', end='2019-06-30')


st.subheader('Data from 2018 -2019')
st.write(df.describe())

st.subheader('closing price vs time chart')
plt.xlabel('closing price')
plt.ylabel('time chart')
fig = plt.figure(figsize=(12,6))
fig = plt.figure(figsize=(13,8))

plt.plot(df.Close,'r',label='profit',color="red",linewidth=3)
plt.plot(df.Close,'b',label='loss',color="blue",linewidth=2)
st.pyplot(fig)
plt.show()


st.subheader('closing price vs time chart with 100MA & 200MA(AVERAGE)')
ma100 = df.Close.rolling(100).mean()
ma200 = df.Close.rolling(200).mean()
fig = plt.figure(figsize=(12,6))

plt.plot(ma100)
plt.plot(ma100)
plt.plot(df.Close)
st.pyplot(fig)
