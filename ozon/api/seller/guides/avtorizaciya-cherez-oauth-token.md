---
title: Авторизация через OAuth-токен
api: ozon-seller
tag: OAuth-token
group: Общее описание
kind: guide
source: "https://docs.ozon.ru/api/seller/"
content_sha: 1e738d40eeadf3dc
---

# Авторизация через OAuth-токен

Чтобы получить OAuth-токен для доступа к Seller API, создайте [частное](https://docs.ozon.ru/api/applications/#section/Rabota-s-chastnym-prilozheniem)
или [публичное](https://docs.ozon.ru/api/applications/#section/Rabota-s-publichnym-prilozheniem) приложение и выдайте ему
доступ к вашему личному кабинету. После этого вы получите OAuth-токен, который позволит работать с методами Seller API.

Используйте OAuth-токен с методами Seller API согласно уровням доступа, которые вы назначили приложению.

Пример запроса:

```json
POST https://api-seller.ozon.ru/{эндпоинт метода Seller API}
Authorization: Bearer ACCESS_TOKEN
```
