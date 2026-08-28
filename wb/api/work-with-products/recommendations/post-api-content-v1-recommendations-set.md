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
content_sha: 317a36070611b4b8
---

# Установить рекомендации для товаров

`POST /api/content/v1/recommendations/set`

Описание метода

 Метод доступен по
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

- `errors` — array[object]. Ошибки. При `"isError":true`
  - `mainNm` — string **обязательный**. Значение параметра `nmId`
  - `message` — string **обязательный**. Сообщение об ошибке
  - `recomNm` — string **обязательный**. Значение параметра `recomNm`
- `isError` — boolean **обязательный**. Есть ли ошибки: - `false` — ошибок нет. Запрос полностью успешен - `true` — ошибки есть

**208** — Уже отправлено

- `detail` — string **обязательный**. Детали ответа
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `title` — string **обязательный**. Заголовок ответа

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `title` — string **обязательный**. Заголовок ошибки

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

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
