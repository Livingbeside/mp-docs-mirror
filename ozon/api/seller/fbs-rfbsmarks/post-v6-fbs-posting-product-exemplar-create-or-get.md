---
title: Получить данные созданных экземпляров
api: ozon-seller
method: POST
path: /v6/fbs/posting/product/exemplar/create-or-get
operation_id: PostingAPI_FbsPostingProductExemplarCreateOrGetV6
tags:
  - FBS&rFBSMarks
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 32f704ff0268a12f
---

# Получить данные созданных экземпляров

`POST /v6/fbs/posting/product/exemplar/create-or-get`

Метод для получения информации по экземплярам товаров из отправления, переданных в методе [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6).

Используйте метод для получения `exemplar_id`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Данные экземпляров

- `multi_box_qty` — integer<int32>. Количество коробок, в которые упакован товар.
- `posting_number` — string. Номер отправления.
- `products` — array[object]. Список товаров.
  - `exemplars` — array[object]. Информация об экземплярах.
    - `exemplar_id` — integer<int64>. Идентификатор экземпляра.
    - `gtd` — string. Номер грузовой таможенной декларации (ГТД).
    - `is_gtd_absent` — boolean. Признак того, что не указан номер грузовой таможенной декларации (ГТД).
    - `is_rnpt_absent` — boolean. Признак того, что не указан регистрационный номер партии товара (РНПТ).
    - `marks` — array[object]. Список контрольных идентификационных знаков (КИЗ) и других маркировок в одном экземпляре.
      - `mark` — string. Значение кода маркировки.
      - `mark_type` — string. Тип кода маркировки: - `mandatory_mark` — обязательная маркировка «Честный ЗНАК»; - `jw_uin` — уникальный идентификационный номер (УИН) ювелирного изделия; - `imei` — IMEI мобильного устройства.
    - `rnpt` — string. Регистрационный номер партии товара (РНПТ).
    - `weight` — number<float>. Фактический вес экземпляра.
  - `has_imei` — boolean. Признак наличия IMEI. Если IMEI есть — `true`.
  - `is_gtd_needed` — boolean. Признак того, что необходимо передать номер грузовой таможенной декларации (ГТД) для продукта и отправления.
  - `is_jw_uin_needed` — boolean. Признак того, что необходимо передать уникальный идентификационный номер ювелирного изделия (УИН).
  - `is_mandatory_mark_needed` — boolean. Признак того, что необходимо передать маркировку «Честный ЗНАК».
  - `is_mandatory_mark_possible` — boolean. Признак того, что возможно заполнить маркировку «Честный ЗНАК».
  - `is_rnpt_needed` — boolean. Признак того, что необходимо передать номер партии товара (РНПТ).
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `quantity` — integer<int32>. Количество экземпляров.
  - `is_weight_needed` — boolean. `true`, если товар весовой.
  - `weight_max` — number<float>. Максимальный вес экземпляра.
  - `weight_min` — number<float>. Минимальный вес экземпляра.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
