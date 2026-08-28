---
title: Согласовать заявку на скидку
api: ozon-seller
method: POST
path: /v1/actions/discounts-task/approve
operation_id: promos_task_approve
tags:
  - Promos
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4633614eaca8fb9a
---

# Согласовать заявку на скидку

`POST /v1/actions/discounts-task/approve`

Вы можете согласовывать заявки в статусах: `NEW` — новые, `SEEN` — просмотренные.

## Запрос

**Тело запроса** (`application/json`):

- `tasks` — array[object] **обязательный**. Список заявок.
  - `approved_price` — number<double> **обязательный**. Согласованная цена.
  - `approved_quantity_max` — integer<uint64> **обязательный**. Одобренное максимальное количество товаров.
  - `approved_quantity_min` — integer<uint64> **обязательный**. Одобренное минимальное количество товаров.
  - `id` — integer<uint64> **обязательный**. Идентификатор заявки. Можно получить с помощью метода [/v1/actions/discounts-task/list](#operation/promos_task_list).
  - `seller_comment` — string. Комментарий продавца к заявке.

## Ответы

**200** — Заявки согласованы

- `result` — object. Результат работы метода.
  - `fail_count` — integer<int32>. Количество заявок, у которых не удалось сменить статус.
  - `fail_details` — array[object]. Ошибки при создании заявки.
    - `error_for_user` — string. Текст ошибки.
    - `task_id` — integer<uint64>. Идентификатор заявки.
  - `success_count` — integer<int32>. Количество заявок с успешной сменой статуса.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
