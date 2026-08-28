---
title: Отчёт об отправлениях
api: ozon-seller
method: POST
path: /v1/report/postings/create
operation_id: ReportAPI_CreateCompanyPostingsReport
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ec45e940d3ad0907
---

# Отчёт об отправлениях

`POST /v1/report/postings/create`

Отчёт об отправлениях с информацией по заказам:
 - статусы заказов,
 - дата начала обработки,
 - номера заказов,
 - номера отправлений,
 - стоимость отправлений,
 - содержимое отправлений.
Соответствует разделу **FBO → Заказы со склада Ozon** и **FBS → Заказы с моих складов → CSV** в личном кабинете.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object **обязательный**. Фильтр.
  - `cancel_reason_id` — array[integer<int64>]. Идентификатор причины отмены.
  - `delivery_method_id` — array[integer<int64>]. Идентификатор способа доставки. Получите методом [/v1/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodList).
  - `delivery_schema` — array[string] **обязательный**. Схема работы — FBO или FBS. За один запрос вы можете передать только одно значение: * `fbo` — чтобы получить отчёт по схеме FBO, * `fbs` — чтобы получить отчёт по схеме FBS.
  - `is_express` — bool. Экспресс-доставка: - `true` — только отправления с доставкой Ozon Express; - `false` — только отправления без доставки Ozon Express. Если ничего не передать, вернутся все отправления.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `processed_at_from` — string<date-time> **обязательный**. Время, когда заказ попал в обработку.
  - `processed_at_to` — string<date-time> **обязательный**. Время, когда заказ появился в личном кабинете.
  - `sku` — array[integer<int64>]. Идентификатор товара в системе Ozon — SKU.
  - `status_alias` — array[string]. Текст статуса.
  - `statuses` — array[integer<int64>]. Числовой статус.
  - `title` — string. Название товара.
  - `warehouse_id` — array[integer<int64>]. Идентификатор склада.
- `language` — string. Язык ответа: - `RU` — русский, - `EN` — английский. По умолчанию: `DEFAULT`.
- `with` — object. Дополнительные поля, которые нужно добавить в ответ.
  - `additional_data` — boolean. `true`, чтобы добавить в ответ дополнительную информацию.
  - `analytics_data` — boolean. `true`, чтобы добавить в ответ аналитику. Передайте значение `filter.delivery_schema = fbs`, иначе вернётся ошибка.
  - `customer_data` — boolean. `true`, чтобы добавить в ответ информацию о покупателе.
  - `jewelry_codes` — boolean. `true`, чтобы добавить в ответ информацию о ювелирных изделиях.

## Ответы

**200** — Отчёт об отправлениях

- `result` — object. Результаты запроса.
  - `code` — string. Уникальный идентификатор отчёта. По нему вы можете получить отчёт в течение 3 дней после запроса. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).

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
