---
title: Список рекомендаций в карточках товаров
api: wb-work-with-products
method: POST
path: /api/content/v1/recommendations/list
operation_id: postV1RecommendationsList
tags:
  - recommendations
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 9b869f268f67fd22
---

# Список рекомендаций в карточках товаров

`POST /api/content/v1/recommendations/list`

Описание метода

 Метод доступен по
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
  - `brandName` — string **обязательный**. Бренд
  - `imtId` — integer<int64> **обязательный**. ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
  - `nmId` — integer **обязательный**. Артикул WB
  - `pic` — string **обязательный**. URL основного изображения в карточке товара
  - `picsCount` — integer **обязательный**. Количество изображений в карточке товара
  - `recomCount` — integer **обязательный**. Количество рекомендуемых товаров
  - `recomNms` — array[integer] **обязательный**. Список `nmId` рекомендуемых товаров
  - `recomPics` — array[string] **обязательный**. Список URL основных изображений рекомендуемых товаров
  - `subjectName` — string **обязательный**. Предмет
  - `title` — string **обязательный**. Название товара
  - `updatedAt` — string<date-time>. Дата и время последнего обновления рекомендаций
  - `vendorCode` — string **обязательный**. Артикул продавца
- `next` — integer **обязательный**. Курсор. Последний `nmId` в ответе

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
