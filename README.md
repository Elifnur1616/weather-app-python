# weather-app-python


import requests

def get_weather(city):
    api_key ="90685248037cdc97043f4a823ede5593"
    url = f"http://api.openweathermap.org/data/2.5/weather?q={city}&appid={api_key}&units=metric&lang=en"

    response = requests.get(url)

    if response.status_code == 200:
        data = response.json()
        main = data['main']
        weather = data['weather'][0]

        print(f"Şehir: {city}")
        print(f"Sıcaklık: {main['temp']}°C")
        print(f"Durum: {weather['description']}")
        print(f"Nem: {main['humidity']}%")
    else:
        print("Şehir bulunamadı ya da API hatası.")


city = input("Şehir adı girin: ")
get_weather(city)
