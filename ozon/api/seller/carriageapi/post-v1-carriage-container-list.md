---
title: Получить список грузомест
api: ozon-seller
method: POST
path: /v1/carriage/container/list
operation_id: CarriageContainerList
tags:
  - CarriageAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 03bebe6ab68f2ce0
---

# Получить список грузомест

`POST /v1/carriage/container/list`

Вы можете оставить обратную связь по этому методу в комментариях к обсуждению в [сообществе разработчиков Ozon for dev](https://dev.ozon.ru/community/2059-Beta-metody-dlia-raboty-s-doveritelnoi-priemkoi/).

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object. Фильтр.
  - `cargo_type` — string. Тип грузоместа: - `box` — коробка; - `pallet` — палета.
  - `created_from` — string<date-time> **обязательный**. Дата начала периода создания грузоместа.
  - `created_to` — string<date-time> **обязательный**. Дата окончания периода создания грузоместа.
  - `sort_type` — string **обязательный**. Тип сортировки грузоместа: - `sort` — сортируемый; - `non-sort` — несортируемый.
  - `statuses` — array[string]. Статус грузоместа: - `new` — создано, но не подтверждено; - `formed` — подтверждено; - `acceptance_in_progress` — началась приёмка в СЦ; - `cancelled` — расформировано из-за непривоза или отмены продавцом; - `finished` — расформировано на СЦ; - `approve_enqueued` — система поставила задачу на подтверждение состава грузоместа; - `approve_in_process` — подтверждение состава грузоместа в процессе; - `approved` — состав грузоместа подтверждён; - `approve_failed` — не удалось подтвердить состав грузоместа, оно осталось пустым; - `added` — добавлено на палету; - `cancellation_enqueded` — система поставила задачу на отмену грузоместа.
  - `warehouse_id` — integer<int64>. Идентификатор склада продавца.
- `limit` — integer<int64>. Количество значений в ответе. Значение по умолчанию — 100.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию; - `DESC` — по убыванию. По умолчанию: `ASC`.

## Ответы

**200** — Список грузомест

- `containers` — array[object]. Информация о грузоместах.
  - `available_actions` — array[string]. Действия с грузоместом: - `approve` — подтвердить состав; - `get_label_container` — получить этикетку; - `delete` — удалить; - `place_box_into_pallet` — добавить коробку на палету; - `remove_box_from_pallet` — убрать коробку с палеты; - `place_posting_into_container` — перенести отправление в другое грузоместо; - `remove_posting_from_container` — убрать отправление из грузоместа; - `get_documents` — получить транспортную накладную.
  - `cargo_type` — string. Тип грузоместа.
  - `container_id` — integer<int64>. Идентификатор грузоместа.
  - `container_number` — integer<int32>. Порядковый номер грузоместа.
  - `count_of_postings` — integer<int32>. Количество отправлений в грузоместе.
  - `created_at` — string<date-time>. Дата создания грузоместа в UTC.
  - `related_containers` — array[?]. Дочерние грузоместа.
  - `sort_type` — string. Тип сортировки грузоместа: - `sort` — сортируемый; - `non-sort` — несортируемый.
  - `status` — string. Статус грузоместа.
  - `warehouse_date` — string. Дата создания грузоместа в часовом поясе склада.
  - `warehouse_id` — integer<int64>. Идентификатор склада продавца.
  - `warehouse_name` — string. Название склада.
  - `weight` — number<float>. Суммарный вес отправлений в грузоместе, кг.
- `cursor` — string. Указатель для выборки следующих данных. Если параметр пустой, данных больше нет.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
