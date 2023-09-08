# Weather-Detect
While using some lib of python and with the help of API i will create the weather detection prog  in which we can give city name as a input and all the details of weather will generate as a output .
also i worked in a gtts lib through which i convert that output into a speech(voice) format. 
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
import requests
import json
import gtts
import playsound

city=input("E")
url=f"https://api.weatherapi.com/v1/current.json?key=a891e37874f94619b80181343232106&q={city}"
r=requests.get(url)
print(r.text)

w=json.loads(r.text)

p=w["current"]["temp_c"]
q=w["location"]["name"]
y=w["location"]["localtime"]
g=w["current"]["condition"]["text"]
v=g=w["current"]["wind_mph"]

f="location in"+str(q)+"current temprature is:"+str(p)+"and climate is"+str(g)+"and current time is"+str(y)

s=gtts.gTTS(f, lang='en')
s.save("r.mp3")
playsound.playsound("r.mp3")
