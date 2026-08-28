---
title: Получить статус добавления экземпляров
api: ozon-seller
method: POST
path: /v5/fbs/posting/product/exemplar/status
operation_id: PostingAPI_FbsPostingProductExemplarStatusV5
tags:
  - FBS&rFBSMarks
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 78e1c57a89f13962
---

# Получить статус добавления экземпляров

`POST /v5/fbs/posting/product/exemplar/status`

Метод для получения статусов добавления экземпляров, переданных в методе [/v6/fbs/posting/product/exemplar/set](#operation/PostingAPI_FbsPostingProductExemplarSetV6). Также возвращает данные по этим экземплярам.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Статусы проверки экземпляров

- `posting_number` — string. Номер отправления.
- `products` — array[object]. Список товаров.
  - `exemplars` — array[object]. Информация об экземплярах.
    - `exemplar_id` — integer<int64>. Идентификатор экземпляра.
    - `gtd` — string. Номер грузовой таможенной декларации (ГТД).
    - `gtd_check_status` — string. Статус проверки грузовой таможенной декларации.
    - `gtd_error_codes` — array[string]. Коды ошибок при проверке грузовой таможенной декларации.
    - `is_gtd_absent` — boolean. Признак того, что не указан номер таможенной декларации (ГТД).
    - `is_rnpt_absent` — boolean. Признак того, что не указан регистрационный номер партии товара (РНПТ).
    - `marks` — array[object]. Список контрольных идентификационных знаков (КИЗ) и других маркировок в одном экземпляре.
      - `check_status` — string. Статус проверки: - `processing` — на проверке; - `failed` — система не успела обработать запрос; - `passed` — заказ готов к сборке.
      - `error_codes` — array[string]. Ошибки при проверке контрольных идентификационных знаков (КИЗ) и других маркировок.
      - `mark` — string. Значение кода маркировки.
      - `mark_type` — string. Тип кода маркировки: - `mandatory_mark` — обязательная маркировка «Честный ЗНАК»; - `jw_uin` — уникальный идентификационный номер (УИН) ювелирного изделия; - `imei` — IMEI мобильного устройства.
    - `rnpt` — string. Регистрационный номер партии товара (РНПТ).
    - `rnpt_check_status` — string. Статус проверки регистрационного номера партии товара.
    - `rnpt_error_codes` — array[string]. Коды ошибок при проверке регистрационного номера партии товара.
    - `weight` — number<float>. Фактический вес экземпляра.
    - `weight_check_status` — string. Статус проверки фактического веса.
    - `weight_error_codes` — array[string]. Коды ошибок при проверке фактического веса.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
- `status` — string. Статус проверки всех экземпляров и доступности сборки: - `ship_available` — сборка доступна; - `ship_not_available` — сборка недоступна; - `validation_in_process` — экземпляры на проверке; - `update_available` — редактирование информации об экземплярах доступно; - `update_not_available` — редактирование информации об экземплярах недоступно.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
