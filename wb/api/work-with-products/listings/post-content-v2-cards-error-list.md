---
title: Список несозданных карточек товаров с ошибками
api: wb-work-with-products
method: POST
path: /content/v2/cards/error/list
operation_id: post-content-v2-cards-error-list
tags:
  - listings
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 6c350b2871697bf8
---

# Список несозданных карточек товаров с ошибками

`POST /content/v2/cards/error/list`

Описание метода

Метод возвращает список карточек товаров ([черновиков](https://seller.wildberries.ru/new-goods/error-cards)), при создании или редактировании которых произошли ошибки, с описанием этих ошибок.

Данные в ответе возвращаются пакетами `batch`. Один пакет содержит:
 - все ошибки по одному массиву `variants` одного запроса при [создании](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post) карточек товаров
 - все ошибки одного запроса при [создании с присоединением](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload~1add/post) или [редактировании](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post) карточек товаров

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

 [получения лимитов карточек товаров](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1limits/get)

 [получения несозданных карточек товаров с ошибками](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1error~1list/post)

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
  - `batchUUID` — string<UUID>. ID последнего пакета в ответе на предыдущий запрос
  - `limit` — number<int>. Количество пакетов в ответе По умолчанию: `100`.
  - `updatedAt` — string<date-time>. Дата и время формирования последнего пакета в ответе на предыдущий запрос
- `order` — object. Порядок выдачи пакетов
  - `ascending` — boolean. - `false` — сортировка по убыванию - `true` — сортировка по возрастанию По умолчанию: `True`.

## Ответы

**200** — Успешно

- `additionalErrors` — object **обязательный**. Дополнительные ошибки
- `data` — object **обязательный**. Данные ответа
  - `cursor` — object **обязательный**. Пагинатор
    - `batchUUID` — string<UUID> **обязательный**. ID последнего пакета в ответе
    - `next` — boolean **обязательный**. Есть ли ещё черновики: - `false` — нет - `true` — да
    - `updatedAt` — string<date-time> **обязательный**. Дата и время формирования последнего пакета в ответе
  - `items` — array[object] **обязательный**. Пакеты данных
    - `batchUUID` — string<UUID> **обязательный**. ID пакета
    - `brands` — object **обязательный**. Бренды. Разбивка по `vendorCodes`
    - `errors` — object **обязательный**. Ошибки. Разбивка по `vendorCodes`
    - `subjects` — object **обязательный**. Предметы. Разбивка по `vendorCodes`
    - `updatedAt` — string<date-time> **обязательный**. Дата и время создания или редактирования пакета
    - `vendorCodes` — array[string] **обязательный**. Артикулы продавца
- `error` — boolean **обязательный**. Флаг ошибки
- `errorText` — string **обязательный**. Описание ошибки

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
