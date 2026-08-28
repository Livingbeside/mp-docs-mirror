---
title: Получить список заявок на отмену rFBS
api: ozon-seller
method: POST
path: /v2/conditional-cancellation/list
operation_id: CancellationAPI_GetConditionalCancellationListV2
tags:
  - CancellationAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ec7060640a31e19b
---

# Получить список заявок на отмену rFBS

`POST /v2/conditional-cancellation/list`

Метод для получения списка заявок на отмену rFBS-заказов.

## Запрос

**Тело запроса** (`application/json`):

- `filters` — object. Фильтры.
  - `cancellation_initiator` — array[string (OZON, SELLER, CLIENT, SYSTEM, DELIVERY)]. Инициатор отмены: - `SELLER` — продавец, - `CLIENT` — покупатель, - `OZON` — Ozon, - `SYSTEM` — система, - `DELIVERY` — служба доставки.
  - `posting_number` — array[string]. Фильтр по номеру отправления.
  - `state` — string (ALL, ON_APPROVAL, APPROVED, REJECTED). Фильтр по статусу заявки на отмену: - `ALL` — заявки в любом статусе, - `ON_APPROVAL` — заявки на рассмотрении, - `APPROVED` — подтверждённые заявки, - `REJECTED` — отклонённые заявки. По умолчанию: `ALL`.
- `last_id` — integer<int64>. Идентификатор последнего значения на странице. Оставьте это поле пустым при выполнении первого запроса. Чтобы получить следующие значения, укажите `last_id` из ответа предыдущего запроса.
- `limit` — integer<int32> **обязательный**. Количество заявок в ответе.
- `with` — object. Дополнительная информация.
  - `counter` — boolean. Признак, что в ответе нужно вывести счётчик заявок в статусе `ON_APPROVAL`.

## Ответы

**200** — Список заявок на отмену

- `counter` — integer<int64>. Cчётчик заявок в статусе `ON_APPROVAL`.
- `last_id` — integer<int64>. Идентификатор последнего значения на странице. Чтобы получить следующие значения, передайте полученное значение в следующем запросе в параметре `last_id`.
- `result` — array[object]. Информация о заявках на отмену.
  - `approve_comment` — string. Комментарий, оставленный при подтверждении или отклонении заявки на отмену.
  - `approve_date` — string<date-time>. Дата подтверждения или отклонения заявки на отмену.
  - `auto_approve_date` — string<date-time>. Дата, после которой заявка будет автоматически подтверждена.
  - `cancellation_id` — integer<int64>. Идентификатор заявки на отмену.
  - `cancellation_initiator` — string (OZON, SELLER, CLIENT, SYSTEM, DELIVERY). Инициатор отмены: - `SELLER` — продавец, - `CLIENT` — покупатель, - `OZON` — Ozon, - `SYSTEM` — система, - `DELIVERY` — служба доставки.
  - `cancellation_reason` — object. Причина отмены.
    - `id` — integer<int64>. Идентификатор причины отмены.
    - `name` — string. Название причины отмены.
  - `cancellation_reason_message` — string. Комментарий к заявке на отмену, введённый инициатором отмены вручную.
  - `cancelled_at` — string<date-time>. Дата создания заявки на отмену.
  - `order_date` — string<date-time>. Дата создания заказа.
  - `posting_number` — string. Номер отправления.
  - `source_id` — integer<int64>. Предыдущий идентификатор заявки на отмену. Используется для поддержания обратной совместимости.
  - `state` — object. Статус заявки на отмену.
    - `id` — integer<int64>. Идентификатор статуса.
    - `name` — string. Название статуса.
    - `state` — string (ON_APPROVAL, APPROVED, REJECTED). Статус заявки: - `ON_APPROVAL` — заявка на рассмотрении, - `APPROVED` — подтверждённая заявка, - `REJECTED` — отклонённая заявка.
  - `tpl_integration_type` — string. Тип интеграции со службой доставки.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
