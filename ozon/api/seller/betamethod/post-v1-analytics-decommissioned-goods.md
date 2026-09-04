---
title: Получить отчёт о списанных товарах
api: ozon-seller
method: POST
path: /v1/analytics/decommissioned-goods
operation_id: AnalyticsDecommissionedGoods
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 72765367c4d8ca2b
---

# Получить отчёт о списанных товарах

`POST /v1/analytics/decommissioned-goods`

Соответствует разделу **FBO → Списанные товары** в личном кабинете.

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2287-Novyi-metod-dlia-polucheniia-Otcheta-spisannye-tovary/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object **обязательный**. Фильтры.
  - `compensation` — array[string (NO_COMPENSATION, PRELIMINARY_COMPENSATION, CLOSED_COMPENSATION)]. Тип компенсации: - `NO_COMPENSATION` — без компенсации; - `PRELIMINARY_COMPENSATION` — предварительная компенсация; - `CLOSED_COMPENSATION` — выплаченная компенсация.
  - `date_from` — string<date-time> **обязательный**. Дата, с которой данные отображаются в отчёте.
  - `date_to` — string<date-time> **обязательный**. Дата, по которую данные отображаются в отчёте.
  - `delivery_schema` — string (FBO, FBS) **обязательный**. Схема доставки: - `FBO` — доставка со склада Ozon; - `FBS` — доставка со своего склада.
  - `dispose_reasons` — array[string (ECONOM_UTILIZATION, SELLER_UTILIZATION, MISSED_DEADLINE, MISSED_COURIER_DELIVERY, PROHIBITED_FOR_SALE, EXPIRED, DAMAGED_DUE_TO_PACKAGING, DAMAGED_BY_CUSTOMER, SPILLED_DUE_TO_PACKAGING, OZON_DEFECT, OZON_LOSS, OTHER…)]. Причина списания: - `ECONOM_UTILIZATION` — возвраты по тарифу «Эконом»; - `SELLER_UTILIZATION` — вы заказали утилизацию; - `MISSED_DEADLINE` — вы не забрали возврат в срок; - `MISSED_COURIER_DELIVERY` — вы не приняли возврат у курьера; - `PROHIBITED_FOR_SALE` — товар запрещён к продаже; - `EXPIRED` — истёк срок годности товара; - `DAMAGED_DUE_TO_PACKAGING` — товар повреждён во время упаковки; - `DAMAGED_BY_CUSTOMER` — товар повреждён покупателем; - `SPILLED_DUE_TO_PACKAGING` — товар пролился или просыпался во время упаковки; - `OZON_DEFECT` — брак по вине Ozon; - `OZON_LOSS` — потеря по вине Ozon; - `OTHER` — прочие причины; - `REZON` — не определена; - `AUTODISPOSAL_STOCK` — автоутилизация со стока; - `RETURNS_AUTO_INVALID` — автоутилизация возвратов и отмен невалидных товаров; - `RETURNS_AUTO_VALID` — автоутилизация возвратов и отмен валидных товаров; - `TRUSTBASED_ACCEPTANCE` — списание по доверительной приёмке.
  - `posting_number` — string. Номер отправления.
  - `skus` — array[string<int64>]. Идентификаторы товаров в системе Ozon — SKU.
  - `supply_id` — integer<int64>. Идентификатор поставки.
- `page` — integer<int32> **обязательный**. Номер страницы, возвращаемой в запросе.
- `page_size` — integer<int32> **обязательный**. Количество элементов на странице.
- `sort_by` — string (DATE, DISPOSAL_FEE). Тип сортировки: - `DATE` — по дате; - `DISPOSAL_FEE` — по начислению.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию.

## Ответы

**200** — Отчёт о списанных товарах

- `items` — array[object]. Информация о товарах.
  - `compensation_price` — number<double>. Сумма выплаченной компенсации.
  - `compensation_type` — string (NO_COMPENSATION, PRELIMINARY_COMPENSATION, CLOSED_COMPENSATION). Тип компенсации: - `NO_COMPENSATION` — без компенсации; - `PRELIMINARY_COMPENSATION` — предварительная компенсация; - `CLOSED_COMPENSATION` — выплаченная компенсация.
  - `date` — string<date-time>. Дата списания товара.
  - `delivery_schema` — string (FBO, FBS). Схема доставки: - `FBO` — доставка со склада Ozon; - `FBS` — доставка со своего склада.
  - `disposal_fee` — number<double>. Начисление за утилизацию товара.
  - `dispose_reason` — string (ECONOM_UTILIZATION, SELLER_UTILIZATION, MISSED_DEADLINE, MISSED_COURIER_DELIVERY, PROHIBITED_FOR_SALE, EXPIRED, DAMAGED_DUE_TO_PACKAGING, DAMAGED_BY_CUSTOMER, SPILLED_DUE_TO_PACKAGING, OZON_DEFECT, OZON_LOSS, OTHER…). Причина списания: - `ECONOM_UTILIZATION` — возвраты по тарифу «Эконом»; - `SELLER_UTILIZATION` — вы заказали утилизацию; - `MISSED_DEADLINE` — вы не забрали возврат в срок; - `MISSED_COURIER_DELIVERY` — вы не приняли возврат у курьера; - `PROHIBITED_FOR_SALE` — товар запрещён к продаже; - `EXPIRED` — истёк срок годности товара; - `DAMAGED_DUE_TO_PACKAGING` — товар повреждён во время упаковки; - `DAMAGED_BY_CUSTOMER` — товар повреждён покупателем; - `SPILLED_DUE_TO_PACKAGING` — товар пролился или просыпался во время упаковки; - `OZON_DEFECT` — брак по вине Ozon; - `OZON_LOSS` — потеря по вине Ozon; - `OTHER` — прочие причины; - `REZON` — не определена; - `AUTODISPOSAL_STOCK` — автоутилизация со стока; - `RETURNS_AUTO_INVALID` — автоутилизация возвратов и отмен невалидных товаров; - `RETURNS_AUTO_VALID` — автоутилизация возвратов и отмен валидных товаров; - `TRUSTBASED_ACCEPTANCE` — списание по доверительной приёмке.
  - `posting_number` — string. Номер отправления.
  - `quantity` — integer<int32>. Количество товаров в списании.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `supply_id` — integer<int64>. Идентификатор поставки.
- `total_count` — integer<int32>. Количество оставшихся товаров, которые можно получить в ответе.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
