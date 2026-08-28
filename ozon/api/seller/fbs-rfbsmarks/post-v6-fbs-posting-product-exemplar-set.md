---
title: Проверить и сохранить данные экземпляров
api: ozon-seller
method: POST
path: /v6/fbs/posting/product/exemplar/set
operation_id: PostingAPI_FbsPostingProductExemplarSetV6
tags:
  - FBS&rFBSMarks
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 1a8fd07300fcdc82
---

# Проверить и сохранить данные экземпляров

`POST /v6/fbs/posting/product/exemplar/set`

Асинхронный метод:
- для проверки наличия экземпляров в обороте в системе «Честный ЗНАК»;
- для сохранения данных экземпляров. 

Чтобы получить результаты проверок, используйте метод [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5). 
Для получения данных о созданных экземплярах, используйте метод [/v6/fbs/posting/product/exemplar/create-or-get](#operation/PostingAPI_FbsPostingProductExemplarCreateOrGetV6).

Если у вас несколько одинаковых товаров в отправлении, укажите один `product_id` и массив `exemplars` для каждого товара из отправления.

Всегда передавайте полный набор данных по экземплярам и продуктам. 

Например, в вашей системе 10 экземпляров. 
Вы передали их для проверки и сохранения. 
Потом добавили в своей системе ещё 60 экземпляров.
При повторной передаче экземпляров для проверки и сохранения укажите все экземпляры: и старые, и только что добавленные.

Код ответа 200 не гарантирует, что данные об экземплярах приняты. 
Он указывает, что создана задача для добавления информации. 
Чтобы проверить статус задачи, используйте метод [/v5/fbs/posting/product/exemplar/status](#operation/PostingAPI_FbsPostingProductExemplarStatusV5).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `multi_box_qty` — integer<int32>. Количество коробок, в которые упакован товар.
- `posting_number` — string **обязательный**. Номер отправления.
- `products` — array[object] **обязательный**. Список товаров.
  - `exemplars` — array[object] **обязательный**. Информация об экземплярах.
    - `exemplar_id` — integer<int64> **обязательный**. Идентификатор экземпляра.
    - `gtd` — string. Номер грузовой таможенной декларации (ГТД).
    - `is_gtd_absent` — boolean. Признак того, что не указан номер грузовой таможенной декларации (ГТД).
    - `is_rnpt_absent` — boolean. Признак того, что не указан регистрационный номер партии товара (РНПТ).
    - `marks` — array[object]. Список контрольных идентификационных знаков (КИЗ) и других маркировок в одном экземпляре.
      - `mark` — string. Значение кода маркировки.
      - `mark_type` — string. Тип кода маркировки: - `mandatory_mark` — обязательная маркировка «Честный ЗНАК»; - `jw_uin` — уникальный идентификационный номер (УИН) ювелирного изделия; - `imei` — IMEI мобильного устройства.
    - `rnpt` — string. Регистрационный номер партии товара (РНПТ).
    - `weight` — number<float>. Фактический вес экземпляра.
  - `product_id` — integer<int64> **обязательный**. Идентификатор товара в системе Ozon — SKU.

## Ответы

**200** — Запрос обработан

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
