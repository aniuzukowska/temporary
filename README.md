# Allure notifications
**Allure notifications** - это библиотека, которая позволяет выполнять автоматическое оповещение о результатах прохождения автотестов, которое направляется в нужный вам мессенджер (Telegram, Slack, Skype, Email, Mattermost).

Languages: 🇬🇧 🇫🇷 🇷🇺 🇺🇦 🇧🇾 🇨🇳
 
## Содержание
+ [Принцип работы](#Принцип)
+ [Как выглядят оповещения](#Примеры)
+ [Как использовать в своем проекте](#Настройка)



 
<a name="Принцип">
 
## Принцип работы
По итогам выполнения автотестов генерируется файл summury.json в папке allure-report/widgets. 
Этот файл содержит общую статистику о результатах прохождения тестов, на основании которой как раз и формируется уведомление, которое отправляет бот (отрисовывается диаграмма и добавляется соответствующий текст).
 
<img width="1021" alt="image" src="https://user-images.githubusercontent.com/109241600/212339206-6ccc946b-9a15-43ca-b380-351fd220b6e7.png">
 
 
 

Пример файла summury.json
```
{
  "reportName" : "Allure Report",
  "testRuns" : [ ],
  "statistic" : {
    "failed" : 182,
    "broken" : 70,
    "skipped" : 118,
    "passed" : 439,
    "unknown" : 42,
    "total" : 851
  },
  "time" : {
    "start" : 1590795193703,
    "stop" : 1590932641296,
    "duration" : 11311,
    "minDuration" : 7901,
    "maxDuration" : 109870,
    "sumDuration" : 150125
  }
}
```
 
 
<a name="Примеры">
 
## Как выглядят оповещения
<img width="828" alt="image" src="https://user-images.githubusercontent.com/109241600/212322072-e5cbc8f8-b749-4711-988c-3129e7081e4a.png">
<img width="828" alt="image" src="https://user-images.githubusercontent.com/109241600/212322156-03cd5455-73d3-4d2a-80ef-7a11dac59959.png">


<a name="Настройка">

## Как использовать в своем проекте
ропорпрп
 
 
 

