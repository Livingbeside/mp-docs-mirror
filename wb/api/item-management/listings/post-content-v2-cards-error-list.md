---
title: Список несозданных карточек товаров с ошибками
api: wb-item-management
method: POST
path: /content/v2/cards/error/list
operation_id: postV2CardsErrorList
tags:
  - listings
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: f6eab5e90aa4a805
---

# Список несозданных карточек товаров с ошибками

`POST /content/v2/cards/error/list`

Описание метода

Метод возвращает список карточек товаров ([черновиков](https://seller.wildberries.ru/new-goods/error-cards)), при создании или редактировании которых произошли ошибки, с описанием этих ошибок.

Данные в ответе возвращаются пакетами `batch`. Один пакет содержит:
 - все ошибки по одному массиву `variants` одного запроса при [создании](./item-management#tag/listingItems/operation/postV2CardsUpload) карточек товаров
 - все ошибки одного запроса при [создании с присоединением](./item-management#tag/listingItems/operation/postV2CardsUploadAdd) или [редактировании](./item-management#tag/listings/operation/postV2CardsUpdate) карточек товаров

Чтобы получить более 100 пакетов, используйте пагинацию:
 1. Сделайте первый запрос: 

 
 {
 "cursor": {
 "limit": 100
 },
 "order": {
 "ascending": true
 }
 }
 2. Скопируйте `"updatedAt":"***","batchUUID":"***" `из `cursor` ответа и вставьте в `cursor` запроса.
 3. Повторите запрос.
 4. Повторяйте пункты 2 и 3, пока не получите в ответе `"next":false`. Это будет означать, что вы получили все пакеты.

 Чтобы удалить карточку товара из списка, сделайте ещё один запрос на создание, создание с присоединением или редактирование карточки товара с исправленными ошибками

Лимит запросов на один аккаунт продавца для методов:

 [получения лимитов карточек товаров](./item-management#tag/listingItems/operation/getV2CardsLimits)

 [получения несозданных карточек товаров с ошибками](./item-management#tag/listings/operation/postV2CardsErrorList)

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 10 запросов | 6 сек | 5 запросов |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string | нет | Язык названий предметов: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — object. Пагинатор
  - `limit` — number<int>. Количество пакетов в ответе По умолчанию: `100`.
  - `updatedAt` — string<date-time>. Дата и время формирования последнего пакета в ответе на предыдущий запрос
  - `batchUUID` — string<UUID>. ID последнего пакета в ответе на предыдущий запрос
- `order` — object. Порядок выдачи пакетов
  - `ascending` — boolean. - `false` — сортировка по убыванию - `true` — сортировка по возрастанию По умолчанию: `True`.

## Ответы

**200** — Успешно

- `data` — object **обязательный**. Данные ответа
  - `items` — array[object] **обязательный**. Пакеты данных
    - `batchUUID` — string<UUID> **обязательный**. ID пакета
    - `subjects` — object **обязательный**. Предметы. Разбивка по `vendorCodes`
    - `brands` — object **обязательный**. Бренды. Разбивка по `vendorCodes`
    - `vendorCodes` — array[string] **обязательный**. Артикулы продавца
    - `errors` — object **обязательный**. Ошибки. Разбивка по `vendorCodes`
    - `updatedAt` — string<date-time> **обязательный**. Дата и время создания или редактирования пакета
  - `cursor` — object **обязательный**. Пагинатор
    - `next` — boolean **обязательный**. Есть ли ещё черновики: - `false` — нет - `true` — да
    - `updatedAt` — string<date-time> **обязательный**. Дата и время формирования последнего пакета в ответе
    - `batchUUID` — string<UUID> **обязательный**. ID последнего пакета в ответе
- `error` — boolean **обязательный**. Флаг ошибки
- `errorText` — string **обязательный**. Описание ошибки
- `additionalErrors` — object **обязательный**. Дополнительные ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
- `additionalErrors` — object. Дополнительные ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
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
