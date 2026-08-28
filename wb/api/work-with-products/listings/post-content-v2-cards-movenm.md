---
title: Объединение и разъединение карточек товаров
api: wb-work-with-products
method: POST
path: /content/v2/cards/moveNm
operation_id: post-content-v2-cards-movenm
tags:
  - listings
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: fba54301fa82e366
---

# Объединение и разъединение карточек товаров

`POST /content/v2/cards/moveNm`

Описание метода

Метод [объединяет и разъединяет](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточки товаров. Карточки товаров являются объединёнными, если у них одинаковый `imtID`.

Для объединения карточек товаров сделайте запрос **с указанием** `imtID`. Можно объединять не более 30 карточек товаров.

Для разъединения карточек товаров сделайте запрос **без указания** `imtID`. Для разъединенных карточек будут сгенерированы новые `imtID`.

Если вы разъедините одновременно несколько карточек товаров, эти карточки объединятся в одну и получат новый `imtID`.

Чтобы присвоить каждой карточке товара уникальный `imtID`, необходимо передавать по одной карточке товара за запрос.

Максимальный размер запроса 10 Мб.

 Объединить можно карточки товаров только в рамках одного предмета

Лимит запросов на один аккаунт продавца для всех методов категории Контент:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 100 запросов | 600 мс | 5 запросов |

Исключение — методы:

 создания карточек товаров

 создания карточек товаров с присоединением

 редактирования карточек товаров

 восстановления карточек товаров из корзины

 получения списка рекомендаций в карточках товаров

 установки рекомендаций для товаров

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Запрос

**Тело запроса** (`application/json`):

- `nmIDs` — array[integer] **обязательный**. `nmID`, которые необходимо объединить
- `targetIMT` — integer **обязательный**. Существующий `imtID`, под которым необходимо [объединить](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточки товаров
- `nmIDs` — array[integer] **обязательный**. `nmID`, которые необходимо разъединить

## Ответы

**200** — Успешно

- `additionalErrors` — object | string. Дополнительные ошибки
  - `string` — string
  - `error` — string **обязательный**
- `data` — object. Данные ответа
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**400** — Неправильный запрос

- `additionalErrors` — object | string. Дополнительные ошибки
  - `string` — string
  - `error` — string **обязательный**
- `data` — object. Данные ответа
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
- `error` — string

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

- `additionalErrors` — object | string. Дополнительные ошибки
  - `string` — string
  - `error` — string **обязательный**
- `data` — object. Данные ответа
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**413** — Превышен лимит объёма данных в запросе

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
