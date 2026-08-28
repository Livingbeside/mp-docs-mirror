---
title: Рабочая среда
api: ozon-seller
tag: Environment
group: Общее описание
kind: guide
source: "https://docs.ozon.ru/api/seller/"
content_sha: f992f4dda3edebe3
---

# Рабочая среда

## Что такое рабочая среда

Рабочая среда — это ваш магазин. Все отправленные запросы, кроме информационных, могут изменять данные в личном 
кабинете и на сайте Ozon.

**Рабочая среда**: api-seller.ozon.ru

Созданные товары можно посмотреть по ссылке вида: https://www.ozon.ru/context/detail/id/SKU, где вместо «SKU» нужно 
указать значение для созданного товара.

## Формат запроса

```http
GET / HTTP/1.1
Host: api-seller.ozon.ru
Client-Id: 
Api-Key: 
Content-Type: application/json
```

Для проверки корректности формата запроса используйте вкладку **Консоль** над описанием метода или 
[Postman](https://www.postman.com).
