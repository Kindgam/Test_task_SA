# Задание 2

## Описание:

Интернет-магазин "Петрушка Зеленая" преуспевает, расширяется и в мобильном приложении решили создать новый экран, который будет отображать магазины партнеров (см. макеты ниже).

<img width="286" height="597" alt="0acdf185-718a-4b34-9f3f-60f9a64b23d0" src="https://github.com/user-attachments/assets/b0da219c-8a19-4eb6-ab56-941e65aa4d05" />

## Что нужно сделать:

  1. Написать пример REST API запроса, который будет вызываться при переходе пользователя на данный экран.
  2. Привести пример ответа этого REST API в соответствии с макетом. Формат - JSON. Учесть, что при клике на плашку магазина должен осуществляться переход по ссылке на внешний ресурс. 

---
# Решение

## REST API запрос

    curl -X GET "https://petrushka.ru/api/v1/partners"
         -H "Authorization: Bearer ACCESS_TOKEN"
         -H "Accept: application/json"
В задании не указано, отображается ли экран партнеров только для авторизованных пользователей, если экран доступен без авторизации, то заголовок Authorization не требуется. Если список магазинов определяется по геолокации пользователя, то для передачи местоположения/адреса пользователя можно использовать query-параметры.

## Пример ответа REST API

HTTP/1.1 200 OK    
Content-Type: application/json
```json
[
  {
    "id": 1,
    "name": "METRO",
    "imageUrl": "https://petrushka.ru/image/metro.png",
    "delivery": {
      "type": "scheduled",
      "timeStart": "2026-02-10T21:00:00+05:00",
      "timeEnd": "2026-02-10T23:00:00+05:00"
    },
    "redirectUrl": "https://metro-cc.ru/"
  },
  {
    "id": 2,
    "name": "Ашан",
    "imageUrl": "https://petrushka.ru/image/auchan.png",
    "delivery": {
      "type": "scheduled",
      "timeStart": "2026-02-10T18:00:00+05:00",
      "timeEnd": "2026-02-10T20:00:00+05:00"
    },
    "redirectUrl": "https://www.auchan.ru/"
  },
  {
    "id": 3,
    "name": "ВкусВилл",
    "imageUrl": "https://petrushka.ru/image/vkusvill.png",
    "delivery": {
      "type": "fast",
      "minMinutes": 20,
      "maxMinutes": 60
    },
    "redirectUrl": "https://vkusvill.ru"
  },
  {
    "id": 4,
    "name": "Виктория",
    "imageUrl": "https://petrushka.ru/image/victoria.png",
    "delivery": {
      "type": "scheduled",
      "timeStart": "2026-02-10T17:00:00+05:00",
      "timeEnd": "2026-02-10T19:00:00+05:00"
    },
  "redirectUrl": "https://victoria-group.ru/"
  }
]
```
