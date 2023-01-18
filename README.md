# Allure notifications
**Allure notifications** - это библиотека, позволяющая выполнять автоматическое оповещение о результатах прохождения автотестов, которое направляется в нужный вам мессенджер (Telegram, Slack, Skype, Email, Mattermost).

Languages: 🇬🇧 🇫🇷 🇷🇺 🇺🇦 🇧🇾 🇨🇳
 
## Содержание
+ [Принцип работы](#Принцип)
+ [Как выглядят оповещения](#Примеры)
+ [Как использовать в своем проекте:](#Настройка)
   + [Для запуска локально](#Локально)


 
<a name="Принцип">
 
## Принцип работы
По итогам выполнения автотестов генерируется файл summary.json в папке allure-report/widgets. 
Этот файл содержит общую статистику о результатах прохождения тестов, на основании которой как раз и формируется уведомление, которое отправляет бот (отрисовывается диаграмма и добавляется соответствующий текст).
 
<img width="1021" alt="image" src="https://user-images.githubusercontent.com/109241600/213257051-977acd4d-5793-4b2e-b16b-c0e0c6c10194.png">

 

Пример файла summary.json
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

 
<a name="Локально">

### Для запуска локально
1. Создать в корне проекта папку `notifications`.
2. <a href="https://github.com/qa-guru/allure-notifications/releases" target="_blank">Скачать</a> актуальную версию файла `allure-notifications-version.jar`, и разместить его в папке `notifications` в своем проекте.
3. В папке `notifications` создать файл `config.json` со следующей структурой (оставить раздел `Base` и те мессенджеры, на которые требуется отправлять оповещения): 
```
{
  "base": {
    "logo": "",
    "project": "",
    "environment": "",
    "comment": "",
    "reportLink": "",
    "language": "ru",
    "allureFolder": "",
    "enableChart": false
  },
  "telegram": {
    "token": "",
    "chat": "",
    "replyTo": ""
  },
  "slack": {
    "token": "",
    "chat": "",
    "replyTo": ""
  },
  "mattermost": {
    "url": "",
    "token": "",
    "chat": ""
  },
  "skype": {
    "appId": "",
    "appSecret": "",
    "serviceUrl": "",
    "conversationId": "",
    "botId": "",
    "botName": ""
  },
  "mail": {
    "host": "",
    "port": "",
    "username": "",
    "password": "",
    "securityProtocol": null,
    "from": "",
    "recipient": ""
  },
  "proxy": {
    "host": "",
    "port": 0,
    "username": "",
    "password": ""
  }
}
```
Блок `proxy` используется если нужно указать дополнительную конфигурацию proxy.

4. Заполнить в файле `config.json` блок `Base`: 

Пример заполнения блока `Base`:
```
"base": {
    "logo": "logo.png",
    "project": "some project",
    "environment": "some env",
    "comment": "some comment",
    "reportLink": "",
    "language": "en",
    "allureFolder": "build/allure-report/",
    "enableChart": true
  }
```  
Порядок заполнения:
+ `project`, `environment`, `comment` - соответственно имя проекта, название окружения и произвольный комментарий. 
+ `reportLink` - ссылка на Allure report с результатами прохождения автотестов (целесообразно заполнять при запуске автотестов из Jenkins - об этом ниже)
+ `language` - язык, на котором будет сформирован текст для оповещения (варианты: en / fr / ru / ua / by / cn), данный параметр является обязательным
+ `allureFolder` - путь к папке с результатами работы Allure
+ `enableChart` - требуется ли отображать диаграмму (варианты: true / false)
+ `logo` - путь к файлу с логотипом (если заполнено, то в левом верхнем углу диаграммы будет отображаться соответствующий логотип)
 
Пример оповещения с логотипом в левом верхнем углу:

<img width="356" alt="image" src="https://user-images.githubusercontent.com/109241600/213270834-008f90a7-d249-43a8-a997-6a9827c8f1fd.png">


 
 
Чтобы настроить желаемые пункты назначения для уведомлений (telegram, slack, mattermost, skype, mail), имейте в виду, что можно установить несколько пунктов назначения одновременно, если пункт назначения не установлен, то уведомление не будет отправлено и ошибка не будет
 


 


5. Заполнить файл `config.json` в зависимости от вида мессенджера:
+ <a href="https://github.com/qa-guru/allure-notifications/wiki/Telegram-configuration" target="_blank">Telegram config</a>
+ <a href="https://github.com/qa-guru/allure-notifications/wiki/Slack-configuration" target="_blank">Slack config</a>
+ <a href="https://github.com/qa-guru/allure-notifications/wiki/Email-configuration" target="_blank">Email config</a>
+ <a href="https://github.com/qa-guru/allure-notifications/wiki/Skype-configuration" target="_blank">Skype config</a>
+ <a href="https://github.com/qa-guru/allure-notifications/wiki/Mattermost-configuration" target="_blank">Mattermost config</a>


6. Выполнить в командной строке следующую команду:
```
 java "-DconfigFile=${PATH_TO_FILE}" -jar allure-notifications-4.2.1.jar
``` 
Примечание:
 - на момент запуска уже должен быть сформирован файл `summury.json`
 - в тексте команды нужно указать ту версию файла jar, которую вы скачали на предыдущих шагах
 - в тексте команды вместо `${PATH_TO_FILE}` указать путь к файлу `config.json`
 

 

