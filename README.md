# Домашнее задание к занятию «3.1. Docker»
## Задача №1 - PostgreSQL
![image](https://github.com/user-attachments/assets/a6cd8872-30bb-4b92-94a9-ac17205e3d58)

Вам необходимо подготовить приложение к тестированию на СУБД PostgreSQL (используйте образ 12-alpine, если он недоступен, то берите последний опубликованный на DockerHub). Возьмите собранный jar-файл `db-api.jar`, аналогично примеру на лекции положите рядом файл `application.properties`, но в строке:
`jdbc:mysql://...` поменяйте `mysql` на `postgresql`.

Вам нужно дописать остальные настройки (хост, порт, БД, имя пользователя и пароль).

Кроме того, вам нужно подготовить файл `docker-compose.yml`, в котором прописать настройки для запуска контейнера PostgreSQL. Всю информацию о его (контейнера) запуске вы найдёте на официальной странице образа на Docker Hub.

Запустите сначала `docker-compose up` и только после того, как БД запустится, запустите целевое приложение: `java -jar db-api.jar` (если нужно поменять порт запуска, по умолчанию он 9999, то добавьте в файл `application.properties` строку `server.port=<нужный номер порта>`).

Если вы сделали всё правильно, то приложение запустится и на `GET http://localhost:9999/api/cards` выдаст вам JSON с картами:
```json
[ 
   { 
      "id":1,
      "name":"Альфа-Карта Premium",
      "description":"Альфа-Карта вернёт ваши деньги",
      "imageUrl":"/alfa-card-premium.png"
   },
   { 
      "id":2,
      "name":"Alfa Travel Premium",
      "description":"Самая выгодная карта для путешествий",
      "imageUrl":"/alfa-card-travel.png"
   },
   { 
      "id":3,
      "name":"CashBack Premium",
      "description":"Заправь свою карту. Кэшбэк на АЗС, в кафе и ресторанах",
      "imageUrl":"/alfa-card-cashback.png"
   }
]
```

В результате выполнения этой задачи вы должны положить в репозиторий следующие файлы:
* db-api.jar
* application.properties
* docker-compose.yml

**Важно**: для удаления всех данных (и начала с чистого листа) сделайте следующее:
* `docker-compose down` (в каталоге с файлом `docker-compose.yml`)
* удалите каталог для хранения данных `data`
* запустите заново `docker-compose up` (после того, как всё исправите)

Важно: команда `docker-compose rm` (в каталоге с файлом `docker-compose.yml`) удаляет сам контейнер.
