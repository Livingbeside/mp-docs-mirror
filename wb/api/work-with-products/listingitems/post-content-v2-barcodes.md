---
title: Генерация баркодов
api: wb-work-with-products
method: POST
path: /content/v2/barcodes
operation_id: post-content-v2-barcodes
tags:
  - listingItems
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 9e1535cc4e55bbcf
---

# Генерация баркодов

`POST /content/v2/barcodes`

Описание метода

Метод генерирует массив уникальных баркодов для создания размера в [карточке товара](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post). Можно использовать, если у вас нет собственных баркодов.

Лимит запросов на один аккаунт продавца для всех методов категории Контент:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 100 запросов | 600 мс | 5 запросов |

Исключение — методы:

 [создания карточек товаров](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post)

 [создания карточек товаров с присоединением](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload~1add/post)

 [редактирования карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post)

 [восстановления карточек товаров из корзины](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1recover/post)

 [получения списка рекомендаций в карточках товаров](./work-with-products#tag/recommendations/operation/postV1RecommendationsList)

 [установки рекомендаций для товаров](./work-with-products#tag/recommendations/operation/postV1RecommendationsSet)

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Запрос

**Тело запроса** (`application/json`):

- `count` — integer. Кол-во баркодов которые надо сгенерировать, максимальное доступное количество баркодов для генерации - `5 000`

## Ответы

**200** — Успешно

- `additionalErrors` — string. Дополнительные ошибки
- `data` — array[string]. Массив сгенерированных баркодов
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `additionalErrors` — string. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
