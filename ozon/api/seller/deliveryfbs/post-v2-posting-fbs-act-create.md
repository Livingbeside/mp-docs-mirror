---
title: Подтвердить отгрузку и создать документы
api: ozon-seller
method: POST
path: /v2/posting/fbs/act/create
operation_id: PostingAPI_PostingFBSActCreate
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 81f91aeb93c3f624
---

# Подтвердить отгрузку и создать документы

`POST /v2/posting/fbs/act/create`

Метод устаревает и будет отключён 7 сентября 2026. Переключитесь на /v1/carriage/create и /v1/carriage/approve . Подтверждает отгрузку и запускает формирование транспортной накладной и штрихкода для отгрузки. Для продавцов из России также запускается формирование листа отгрузки, а для продавцов из СНГ — акта приёма-передачи. Чтобы сформировать и получить документы, переведите отправление в статус `awaiting_deliver`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `containers_count` — integer<int32>. Количество грузовых мест. Используйте параметр, если вы подключены к доверительной приёмке и отгружаете заказы грузовыми местами. Если вы не подключены к доверительной приёмке, пропустите его. [Подробнее в Базе знаний продавца](https://docs.ozon.ru/partners/prodayoa-so-svoego-sklada-fbs/doveritel-naya-priemka-gruzovogo-mesta)
- `delivery_method_id` — integer<int64> **обязательный**. Идентификатор метода доставки. Для realFBS-складов получите его с помощью метода [/v2/delivery-method/list](#operation/WarehouseAPI_DeliveryMethodListV2). Для FBS-складов используйте значение параметра `warehouse_id`. Его можно получить с помощью метода [/v2/warehouse/list](#operation/WarehouseListV2).
- `departure_date` — string<date-time>. Дата отгрузки.

## Ответы

**200** — Отгрузка подтверждена

- `result` — object. Результат работы метода.
  - `id` — integer<int64>. Номер задания на формирование штрихкода и документов.

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
