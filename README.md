#Importing all the necessary libraries to form the alarm clock:
from tkinter import *
import datetime
import time
import winsound

# import required modules for weather fct 
import requests
import json

#import package for the vocale fct.
from gtts import gTTS
import os
import playsound



# Actuel weather fct (openweather)

#city_name = input("Enter city name : ")
city_name = 'Buffalo'

def current_weather(city_name):
    
    # Give city name 
  
    
    # Enter your API key here 
    api_key = "0f65ec0d6c38ab14c3460cf180d05201"
    
    # base_url variable to store url 
    base_url = "http://api.openweathermap.org/data/2.5/weather?"
    
    
    
    # complete_url variable to store 
    # complete url address 
    complete_url = base_url + "appid=" + api_key + "&q=" + city_name
    
    response = requests.get(complete_url)
    
    #Convert .json to python
    x = response.json()
    
    #If statement to get the wather from response dictionary
    if x["cod"] != "404":
        y = x["main"]
        current_temperature = y["temp"]
        #print("Current weather is", current_temperature)
        return current_temperature
        
#fct for text to speech

def audio(text):
    language ='en'
    output = gTTS(text= text, lang=language, slow=True)
    output.save("output.mp3")
    os.system("start output.mp3")




# fct to set the time

def alarm(set_alarm_timer):
    while True:
        time.sleep(1)
        current_time = datetime.datetime.now()
        now = current_time.strftime("%H:%M:%S")
        date = current_time.strftime("%m/%d/%Y")
        print("The Set Date is:",date)
        print(now)
        print(set_alarm_timer)
        if now != time_elapsed:
            #current_weather(city_name)
            #audio(time_elapsed)
            print("Time to Wake up")
        #winsound.PlaySound("sound.wav",winsound.SND_ASYNC)
        break

def actual_time():
    set_alarm_timer = f"{hour.get()}:{min.get()}:{sec.get()}"
    current_temperature = int(304)
            
    for current_temperature =! 0 :
        
        if current_temperature in range (294, 304):
            #date = datetime.date(1, 1, 1)
            #datetime1 = datetime.datetime.combine(date, set_alarm_timer)
            #datetime2 = datetime.datetime.combine(date, winter)
            #time_elapsed = datetime1 - datetime2
            #print(time_elapsed)
            time_elapsed = set_alarm_timer * winter
            break
        elif current_temperature in range (305, 309):
            #date = datetime.date(1, 1, 1)
            #datetime1 = datetime.datetime.combine(date, set_alarm_timer)
            #datetime2 = datetime.datetime.combine(date, summer)
            #time_elapsed = datetime1 - datetime2
            #print(time_elapsed)
            time_elapsed = set_alarm_timer * summer
            break
        elif current_temperature in range (292, 293):
            #date = datetime.date(1, 1, 1)
            #datetime1 = datetime.datetime.combine(date, set_alarm_timer)
            #datetime2 = datetime.datetime.combine(date, spring)
            #time_elapsed = datetime1 - datetime2
            #print(time_elapsed)
            time_elapsed = set_alarm_timer * spring
            break
        elif current_temperature in range (284, 291):
            #date = datetime.date(1, 1, 1)
            #datetime1 = datetime.datetime.combine(date, set_alarm_timer)
            #datetime2 = datetime.datetime.combine(date, fall)
            #time_elapsed = datetime1 - datetime2
            #print(time_elapsed)
            time_elapsed = set_alarm_timer * fall
            break
        else:
            time_elapsed = set_alarm_timer
            
            return time_elapsed
            
            
    
#time set up after checking outside weather

# Tkinter alarm design

import tkinter

clock = tkinter.Tk()

clock.title("The Seasonnal Alarm")
clock.geometry("400x300")

addTime = tkinter.Label(clock,text = "Hour  Min   Sec",font=60).place(x = 110)
setYourAlarm = tkinter.Label(clock,text = "When to wake you up",fg="blue",relief = "solid",font=("Helevetica",7,"bold")).place(x=0, y=29)

#Weather's widgets

time_format = tkinter.Label(clock, text= "How soon do you want to be waked up", fg="red",bg="black",font="Arial").place(x=70,y=140)
winter = tkinter.Label(clock,text = "Winter (Hour-Min-Sec)",font=60).place(x=10,y=180)
spring = tkinter.Label(clock,text = "Spring (Hour-Min-Sec)",font=60).place(x=10,y=230)
fall = tkinter.Label(clock,text = "Fall (Hour-Min-Sec)",font=60).place(x=200,y=180)
summer = tkinter.Label(clock,text = "Summer (Hour-Min-Sec)",font=60).place(x=200,y=230)


#Added label and entry
#weather_format = tkinter.Label(clock,text = "Current weather",font=60).place(x = 110, y= 20)
#Entry(clock,textvariable = " ",bg = "pink",width = 15).place(x=150,y=50)
current_temperature = Text(clock, height = 1, width = 10).place(x=150,y=55) 

#current_temperature.delete("1.0", END) 
#current_temperature.insert(END, current_temperature)  

# The Variables we require to set the weather alarm
whour = StringVar()
wmin = StringVar()
wsec = StringVar()

phour = StringVar()
pmin = StringVar()
psec = StringVar()

fhour = StringVar()
fmin = StringVar()
fsec = StringVar()

shour = StringVar()
smin = StringVar()
ssec = StringVar()

winter=f"{whour.get()}:{wmin.get()}:{wsec.get()}"
spring=f"{phour.get()}:{pmin.get()}:{psec.get()}"
fall=f"{fhour.get()}:{fmin.get()}:{fsec.get()}"
summer=f"{shour.get()}:{smin.get()}:{ssec.get()}"

# The Variables we require to set the alarm(initialization):
hour = StringVar()
min = StringVar()
fall = StringVar()
sec = StringVar()


#Time required to set the alarm clock:
hourTime= tkinter.Entry(clock,textvariable = hour,bg = "pink",width = 15).place(x=110,y=30)
minTime= tkinter.Entry(clock,textvariable = min,bg = "pink",width = 15).place(x=150,y=30)
secTime = tkinter.Entry(clock,textvariable = sec,bg = "pink",width = 15).place(x=200,y=30)

#Entries to set the weather foe each seasons
winter1 = tkinter.Entry(clock,textvariable = whour,bg = "brown",width = 15).place(x=25,y=205)
winter2 = tkinter.Entry(clock,textvariable = wmin,bg = "brown",width = 15).place(x=50,y=205)
winter3 = tkinter.Entry(clock,textvariable = wsec,bg = "brown",width = 15).place(x=75,y=205)
spring1 = tkinter.Entry(clock,textvariable = phour,bg = "green",width = 15).place(x=25,y=255)
spring2 = tkinter.Entry(clock,textvariable = pmin,bg = "green",width = 15).place(x=50,y=255)
spring3 = tkinter.Entry(clock,textvariable = psec,bg = "green",width = 15).place(x=75,y=255)
fall1 = tkinter.Entry(clock,textvariable = fhour,bg = "red",width = 15).place(x=200,y=205)
fall2 = tkinter.Entry(clock,textvariable = fmin,bg = "red",width = 15).place(x=250,y=205)
fall3= tkinter.Entry(clock,textvariable = fsec,bg = "red",width = 15).place(x=300,y=205)
summer1 = tkinter.Entry(clock,textvariable = shour,bg = "yellow",width = 15).place(x=200,y=255)
summer2 = tkinter.Entry(clock,textvariable = smin,bg = "yellow",width = 15).place(x=250,y=255)
summer3 = tkinter.Entry(clock,textvariable = ssec,bg = "yellow",width = 15).place(x=300,y=255)

#To take the time input by user:
submit = tkinter.Button(clock,text = "Set Alarm",fg="red",width = 10,command = actual_time).place(x =150,y=85)
#submit = tkinter.Button(clock,text = "Set Weather Alarm",fg="red",width = 20,command = time_elapse).place(x =200,y=85)
clock.mainloop()
#Execution of the window.
