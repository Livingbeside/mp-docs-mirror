---
title: Генерация баркодов{{ /content/v2/barcodes }}
api: wb-work-with-products
method: POST
path: /content/v2/barcodes
operation_id: post-content-v2-barcodes
tags:
  - listingItems
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: a10f03c883293ba4
---

# Генерация баркодов{{ /content/v2/barcodes }}

`POST /content/v2/barcodes`

Описание метода Метод генерирует массив уникальных баркодов для создания размера в [карточке товара](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post). Можно использовать, если у вас нет собственных баркодов. Лимит запросов на один аккаунт продавца для всех методов категории Контент : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 100 запросов | 600 мс | 5 запросов | Исключение — методы: создания карточек товаров создания карточек товаров с присоединением редактирования карточек товаров восстановления карточек товаров из корзины получения списка рекомендаций в карточках товаров установки рекомендаций для товаров В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

## Запрос

**Тело запроса** (`application/json`):

- `count` — integer. Кол-во баркодов которые надо сгенерировать, максимальное доступное количество баркодов для генерации - `5 000`

## Ответы

**200** — Успешно

- `data` — array[string]. Массив сгенерированных баркодов
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
- `additionalErrors` — string. Дополнительные ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

**403** — Доступ запрещён

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки
- `additionalErrors` — string. Дополнительные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
