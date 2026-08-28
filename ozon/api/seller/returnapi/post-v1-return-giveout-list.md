---
title: Список возвратных отгрузок
api: ozon-seller
method: POST
path: /v1/return/giveout/list
operation_id: ReturnAPI_GiveoutList
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ee109f3b13419077
---

# Список возвратных отгрузок

`POST /v1/return/giveout/list`

Метод для получения списка активных возвратов. Возвратная отгрузка становится активной после сканирования штрихкода. После сканирования штрихкода второй раз активная выдача переходит в статус неактивной.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `last_id` — integer<int64>. Идентификатор последнего значения на странице.
- `limit` — integer<int64> **обязательный**. Количество элементов в ответе.

## Ответы

**200** — Список возвратных отгрузок

- `giveouts` — array[object]. Идентификатор отгрузки.
  - `approved_articles_count` — integer<int32>. Количество товаров в отгрузке.
  - `created_at` — string<date-time>. Дата и время.
  - `giveout_id` — integer<int64>. Идентификатор отгрузки.
  - `giveout_status` — string. Статусы возвратной отгрузки: - `GIVEOUT_STATUS_UNSPECIFIED` — не определён, напишите в поддержку. - `GIVEOUT_STATUS_CREATED` — создана. - `GIVEOUT_STATUS_APPROVED` — одобрена. - `GIVEOUT_STATUS_COMPLETED` — завершена. - `GIVEOUT_STATUS_CANCELLED` — отменена.
  - `total_articles_count` — integer<int32>. Общее количество товаров, которые нужно забрать со склада.
  - `warehouse_address` — string. Адрес склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада.
  - `warehouse_name` — string. Название склада.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
