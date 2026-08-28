---
title: Перенос карточек товаров в корзину
api: wb-work-with-products
method: POST
path: /content/v2/cards/delete/trash
operation_id: post-content-v2-cards-delete-trash
tags:
  - listings
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: c10f9ed6ed411cfe
---

# Перенос карточек товаров в корзину

`POST /content/v2/cards/delete/trash`

Описание метода

Метод переносит [карточки товаров в корзину](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1trash/post). При этом карточки товаров не удаляются, их можно [восстановить](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1recover/post).

 После переноса в корзину карточке товара присваивается новый imtID — ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров

Карточки товаров удаляются автоматически, если лежат в корзине больше 30 дней, и на них нет остатков. Очистка корзины происходит каждую ночь по московскому времени.

Карточки товаров можно удалить в любое время в [личном кабинете](https://seller.wildberries.ru/new-goods/basket-cards).

Карточка будет продаваться, пока по ней есть остатки на складе, даже если её переместили в корзину. Чтобы полностью снять карточку с продажи, обнулите остатки.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `nmIDs` — array[integer]. Артикулы WB

## Ответы

**200** — Успешно

- `additionalErrors` — object. Дополнительные ошибки
- `data` — object
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**400** — Неправильный запрос

- `additionalErrors` — object. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

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
