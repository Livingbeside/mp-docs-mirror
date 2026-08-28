---
title: Список отчётов
api: ozon-seller
method: POST
path: /v1/report/list
operation_id: ReportAPI_ReportList
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 2961fed714b89af3
---

# Список отчётов

`POST /v1/report/list`

Возвращает список отчётов, которые были сформированы раньше.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `page` — integer<int32> **обязательный**. Номер страницы.
- `page_size` — integer<int32> **обязательный**. Количество значений на странице: - по умолчанию — 100, - маĸсимальное значение — 1000.
- `report_type` — string. Тип отчёта: - `ALL` — все отчёты; - `SELLER_PRODUCTS` — отчёт по товарам; - `SELLER_STOCK` — отчёт об остатках товаров; - `SELLER_RETURNS` — отчёт о возвратах; - `SELLER_POSTINGS` — отчёт об отправлениях; - `SELLER_DISCOUNTED` — отчёт об уценённых товарах; - `MUTUAL_SETTLEMENT` — отчёт о взаиморасчётах; - `DOCUMENT_B2B_SALES` — отчёт о продажах юридическим лицам; - `COMPENSATION_REPORT` — отчёт о компенсациях; - `DECOMPENSATION_REPORT` — отчёт о декомпенсациях; - `MARKED_PRODUCTS_SALES` — отчёт по продажам маркированных товаров; - `SELLER_PLACEMENT_BY_PRODUCTS` — отчёт о стоимости размещения по товарам; - `SELLER_PLACEMENT_BY_SUPPLIES` — отчёт о стоимости размещения по поставкам. По умолчанию: `ALL`.

## Ответы

**200** — Список отчётов

- `result` — object. Результаты запроса.
  - `reports` — array[object]. Массив со всеми сгенерированными отчётами.
    - `additional_data` — array[object]. Дополнительные параметры.
      - `key` — string. Ключ дополнительного параметра.
      - `value` — string. Значение дополнительного параметра.
    - `code` — string. Уникальный идентификатор отчёта. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).
    - `created_at` — string<date-time>. Дата создания отчёта.
    - `error` — string. Код ошибки при генерации отчёта.
    - `expires_at` — string<date-time>. Дата и время, до которых отчёт доступен по ссылке. Поле вернётся пустым, если отчёт сформирован до 14 октября 2025.
    - `file` — string. Ссылка на XLSX-файл. Для отчёта с типом `SELLER_RETURNS` ссылка доступна 5 минут после выполнения запроса.
    - `params` — object. Массив с фильтрами, указанными при создании отчёта продавцом.
    - `report_type` — string. Тип отчёта: - `SELLER_PRODUCTS` — отчёт по товарам; - `SELLER_STOCK` — отчёт об остатках товаров; - `SELLER_RETURNS` — отчёт о возвратах; - `SELLER_POSTINGS` — отчёт об отправлениях; - `SELLER_DISCOUNTED` — отчёт об уценённых товарах; - `MUTUAL_SETTLEMENT` — отчёт о взаиморасчётах; - `DOCUMENT_B2B_SALES` — отчёт о продажах юридическим лицам; - `COMPENSATION_REPORT` — отчёт о компенсациях; - `DECOMPENSATION_REPORT` — отчёт о декомпенсациях; - `MARKED_PRODUCTS_SALES` — отчёт по продажам маркированных товаров; - `SELLER_PLACEMENT_BY_PRODUCTS` — отчёт о стоимости размещения по товарам; - `SELLER_PLACEMENT_BY_SUPPLIES` — отчёт о стоимости размещения по поставкам.
    - `status` — string. Статус генерации отчёта: - `waiting` — в очереди на обработку, - `processing` — обрабатывается, - `success` — отчёт успешно создан, - `failed` — ошибка при создании отчёта.
  - `total` — integer<int32>. Суммарное количество отчётов.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
