---
title: Список актов по отгрузкам
api: ozon-seller
method: POST
path: /v2/posting/fbs/act/list
operation_id: PostingAPI_FbsActList
tags:
  - DeliveryFBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6b2cb00624cc4bd3
---

# Список актов по отгрузкам

`POST /v2/posting/fbs/act/list`

Возвращает список актов по отгрузкам с возможностью отфильтровать отгрузки по периоду, статусу и типу интеграции.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Параметры фильтра.
  - `date_from` — string **обязательный**. Начальная дата создания отгрузок.
  - `date_to` — string **обязательный**. Конечная дата создания отгрузок.
  - `integration_type` — string. Тип интеграции со службой доставки: - `ozon` — доставка силами Ozon. - `aggregator` — доставка внешней службой, Ozon регистрирует заказ. - `3pl_tracking` — доставка внешней службой, продавец регистрирует заказ. - `non_integrated` — доставка силами продавца.
  - `status` — array[string]. Статусы перевозок: - `new` — новая, - `awaiting_retry` — повторная попытка создания, - `in_process` — собирается, - `success` — создана, - `error` — ошибка при создании, - `sended` — отправлена, - `received` — получена, - `formed` — собрана, - `cancelled` — отменена, - `pending` — в очереди на сборку, - `completion_enqueued` — в очереди на завершение, - `completion_processing` — в процессе завершения, - `completion_failed` — ошибка при завершении, - `cancelation_enqueued` — в очереди на отмену, - `cancelation_processing` — в процессе отмены, - `cancelation_failed` — ошибка при отмене, - `completed` — завершена, - `closed` — закрыта.
- `limit` — integer<int64> **обязательный**. Максимальное количество актов в ответе.

## Ответы

**200** — Список актов

- `result` — array[object]. Результат запроса.
  - `id` — int<int64>. Идентификатор отгрузки.
  - `delivery_method_id` — int<int64>. Идентификатор метода доставки.
  - `delivery_method_name` — string. Название метода доставки.
  - `integration_type` — string. Тип интеграции со службой доставки: - `ozon` — доставка через Ozon логистику. - `3pl` — доставка внешней службой, продавец регистрирует заказ.
  - `containers_count` — int<int32>. Число грузовых мест.
  - `status` — string. Статус отгрузки.
  - `departure_date` — string. Дата отгрузки.
  - `created_at` — string<date-time>. Дата создания записи об отгрузке.
  - `updated_at` — string<date-time>. Дата обновления записи об отгрузке.
  - `act_type` — string. Тип акта приёма-передачи для FBS продавцов.
  - `is_partial` — boolean. Признак частичной перевозки. `true`, если перевозка частичная. Частичная перевозка значит, что отгрузка была разделена на несколько частей и по каждой из частей формируются отдельные акты.
  - `has_postings_for_next_carriage` — boolean. Признак наличия подлежащих отгрузке отправлений, которые не попали в текущую перевозку. `true`, если такие отправления есть.
  - `partial_num` — integer<int64>. Порядковый номер частичной перевозки.
  - `related_docs` — object. Информация про акты перевозки.
    - `act_of_acceptance` — object. Информация про акт приёма-передачи.
      - `created_at` — string<date-time>. Дата создания акта.
      - `document_status` — string. Статус акта: - `FORMING` — ещё не готов, - `FORMED` — сформирован, - `CONFIRMED` — подписан Ozon, - `CONFIRMED_WITH_MISMATCH` — подписан Ozon с расхождениями, - `ACCEPTED_BY_CARGO_PLACES` — принят по грузовым местам, - `PRINTED_CARRIAGE` — электронная подпись не нужна, - `ERROR`, `UNKNOWN_ERROR` — ошибка.
    - `act_of_mismatch` — object. Информация про акт о расхождениях.
      - `created_at` — string<date-time>. Дата создания перевозки.
      - `document_status` — string. Статус перевозки или акта: - `NEED_TO_SIGN` — требуется подпись, - `ON_CONFIRMATION` — на подписании Ozon, - `CONFIRMED` — подписан Ozon, - `DISPUTE_OPENED` — принят по грузовым местам, - `PRINTED_CARRIAGE` — электронная подпись не нужна, - `UNKNOWN_ERROR` — ошибка.
    - `act_of_excess` — object. Информация про акт об излишках.
      - `created_at` — string<date-time>. Дата создания акта.
      - `document_status` — string. Статус акта: - `NEED_TO_SIGN` — требуется подпись, - `CONFIRMED` — подписан Ozon, - `UNKNOWN_ERROR` — ошибка.

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
