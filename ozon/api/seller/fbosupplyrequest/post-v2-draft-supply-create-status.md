---
title: Получить информацию о создании заявки на поставку
api: ozon-seller
method: POST
path: /v2/draft/supply/create/status
operation_id: DraftSupplyCreateStatus
tags:
  - FboSupplyRequest
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d597e132737fa976
---

# Получить информацию о создании заявки на поставку

`POST /v2/draft/supply/create/status`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `draft_id` — integer<int64> **обязательный**. Идентификатор черновика. Получите значение параметра методом [/v2/draft/supply/create](#operation/DraftSupplyCreate).

## Ответы

**200** — Информация о создании заявки на поставку

- `error_reasons` — array[string (UNSPECIFIED, SOME_SERVICE_ERROR, ORDER_SKU_LIMIT, INVALID_QUANTITY_OR_QUANT, ORDER_ALREADY_CREATED, ORDER_CREATION_IN_PROGRESS, DRAFT_DOES_NOT_EXIST, CONTRACTOR_CAN_NOT_CREATE_ORDER, INACTIVE_CONTRACT, DRAFT_INCORRECT_STATE, INVALID_VOLUME, INVALID_ROUTE…)]. Причина ошибки: - `UNSPECIFIED` — не определена; - `SOME_SERVICE_ERROR` — ошибка при редактировании поставки; - `ORDER_SKU_LIMIT` — количество товаров в поставке больше 5000; - `INVALID_QUANTITY_OR_QUANT` — некорректное количество товара или грузомест; - `ORDER_ALREADY_CREATED` — заказ уже создан; - `ORDER_CREATION_IN_PROGRESS` — создание заказа в процессе; - `DRAFT_DOES_NOT_EXIST` — черновик не существует; - `CONTRACTOR_CAN_NOT_CREATE_ORDER` — контрагент не может создать заказ; - `INACTIVE_CONTRACT` — нельзя редактировать состав поставки с неактивным договором; - `DRAFT_INCORRECT_STATE` — некорректный статус черновика; - `INVALID_VOLUME` — некорректный объём поставки; - `INVALID_ROUTE` — некорректный маршрут; - `INVALID_STORAGE_WAREHOUSE` — некорректный склад хранения; - `INVALID_STORAGE_REGION` — некорректный регион хранения; - `INVALID_SPLITTING` — некорректное разделение; - `INVALID_SUPPLY_CONTENT` — некорректное содержимое поставки; - `TIMESLOT_NOT_AVAILABLE` — нет доступных таймслотов; - `SKU_DISTRIBUTION_REQUIRED_BUT_NOT_POSSIBLE` — требуется распределение SKU, но оно невозможно; - `XDOCK_IN_DELIVERY_POINT_DISABLED_FOR_SELLER` — поставка кросс-докингом через пункт выдачи заказов недоступна для продавца; - `DRAFT_IS_LOCKED` — черновик заблокирован; - `INVALID_PACKAGE_UNITS_COUNTS` — некорректное количество грузомест; - `SELLER_CONVERSATION_DOES_NOT_EXIST` — точка отгрузки с таким `id` не существует; - `USER_CAN_NOT_CREATE_SELLER_CONVERSATION` — пользователь не может написать продавцу; - `SKU_WITH_ETTN_REQUIRED_TAG_NOT_ALLOWED_FOR_DROP_OFF_POINT` — товар с меткой `is_ettn_required` не разрешён для точки отгрузки; - `INVALID_SELLER_WAREHOUSE` — склад продавца недоступен; - `PICKUP_ORDER_LIMIT_EXCEEDED` — превышен лимит заказов на самовывоз; - `MINIMUM_VOLUME_IN_LITRES_INVALID` — некорректный минимальный объём в литрах; - `INVALID_CLUSTERS_COUNT` — переданы не все кластеры из расчёта; - `UNDEFINED` — неизвестная ошибка.
- `order_id` — integer<int64>. Идентификатор заявки на поставку.
- `status` — string (UNSPECIFIED, SUCCESS, IN_PROGRESS, FAILED). Статус создания заявки на поставку: - `UNSPECIFIED` — не определён, - `SUCCESS` — создана, - `IN_PROGRESS` — создаётся, - `FAILED` — не удалось создать. По умолчанию: `UNSPECIFIED`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
