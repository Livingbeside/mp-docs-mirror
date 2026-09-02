---
title: Список рекомендаций в карточках товаров
api: wb-item-management
method: POST
path: /api/content/v1/recommendations/list
operation_id: postV1RecommendationsList
tags:
  - recommendations
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 38edfa42f594e1e8
---

# Список рекомендаций в карточках товаров

`POST /api/content/v1/recommendations/list`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену, 
 Сервисному токену

Метод возвращает список [рекомендаций](https://seller.wildberries.ru/recommendations-v3) в карточках товаров.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 100 запросов | 600 мс | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `brandNames` — array[string]. Бренды
- `limit` — integer. Количество товаров в ответе По умолчанию: `20`.
- `next` — integer. Курсор. Последний `nmId` в ответе По умолчанию: `0`.
- `search` — string. Поиск: - по артикулу WB `nmId` — полное совпадение - по артикулу продавца `vendorCode` — частичное совпадение
- `subjectIds` — array[integer]. ID предметов

## Ответы

**200** — Успешно

- `data` — array[object] **обязательный**. Данные о товарах и их рекомендациях
  - `nmId` — integer **обязательный**. Артикул WB
  - `imtId` — integer<int64> **обязательный**. ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
  - `vendorCode` — string **обязательный**. Артикул продавца
  - `brandName` — string **обязательный**. Бренд
  - `updatedAt` — string<date-time>. Дата и время последнего обновления рекомендаций
  - `picsCount` — integer **обязательный**. Количество изображений в карточке товара
  - `title` — string **обязательный**. Название товара
  - `subjectName` — string **обязательный**. Предмет
  - `pic` — string **обязательный**. URL основного изображения в карточке товара
  - `recomCount` — integer **обязательный**. Количество рекомендуемых товаров
  - `recomPics` — array[string] **обязательный**. Список URL основных изображений рекомендуемых товаров
  - `recomNms` — array[integer] **обязательный**. Список `nmId` рекомендуемых товаров
- `next` — integer **обязательный**. Курсор. Последний `nmId` в ответе

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
