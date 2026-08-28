---
title: Установить рекомендации для товаров
api: wb-work-with-products
method: POST
path: /api/content/v1/recommendations/set
operation_id: postV1RecommendationsSet
tags:
  - recommendations
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 437fffe646b8e9bc
---

# Установить рекомендации для товаров

`POST /api/content/v1/recommendations/set`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод обновляет, добавляет или удаляет [рекомендации](https://seller.wildberries.ru/recommendations-v3) для товаров.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 100 запросов | 600 мс | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `recList` — array[object] **обязательный**. Список рекомендаций для товаров
  - `nmId` — integer. Артикул WB По умолчанию: `0`.
  - `recommendations` — array[object]. Рекомендуемые товары. Укажите `recomNm` товаров, чтобы добавить их в рекомендации к указанному `nmId`. При отправке пустого массива `[]` все текущие рекомендации для указанного `nmId` будут удалены.
    - `recomNm` — integer. Артикул WB рекомендуемого товара По умолчанию: `0`.
    - `sort` — integer. Позиция товара в списке рекомендаций. Допустимые значения: - `1`–`20` — фиксированная позиция: - при создании или замене (`replace: true`) задаёт порядок отображения - при добавлении (`replace: false`) вставляет товар на указанную позицию, существующие сдвигаются - `0` — автоматическая сортировка товаров: - при создании или замене (`replace: true`) — в порядке расположения товаров в массиве `recommendations` - при добавлении (`replace: false`) — в конец списка существующих рекомендаций, сохраняя порядок из массива `recommendations` По умолчанию: `20`.
- `replace` — boolean. Действие в запросе: - `false` — добавить новые рекомендации к существующим - `true` — заменить существующие рекомендации новыми По умолчанию: `False`.

## Ответы

**200** — Успешно

- `isError` — boolean **обязательный**. Есть ли ошибки: - `false` — ошибок нет. Запрос полностью успешен - `true` — ошибки есть
- `errors` — array[object]. Ошибки. При `"isError":true`
  - `mainNm` — string **обязательный**. Значение параметра `nmId`
  - `recomNm` — string **обязательный**. Значение параметра `recomNm`
  - `message` — string **обязательный**. Сообщение об ошибке

**208** — Уже отправлено

- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `title` — string **обязательный**. Заголовок ответа
- `detail` — string **обязательный**. Детали ответа

**400** — Неправильный запрос

- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
