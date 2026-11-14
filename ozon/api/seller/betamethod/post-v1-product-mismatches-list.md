---
title: Получить несоответствия характеристик товаров
api: ozon-seller
method: POST
path: /v1/product/mismatches/list
operation_id: ProductMismatchesList
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 5dd2cb207dd25917
---

# Получить несоответствия характеристик товаров

`POST /v1/product/mismatches/list`

Метод возвращает информацию о несоответствиях характеристик товаров.
[Подробнее о несоответствиях в Базе знаний продавца](https://seller-edu.ozon.ru/libra/work-with-goods/zagruzka-tovarov/creating-goods/oshibki-pri-rabote-s-kartochkami#несоответствия-между-полями-карточки)

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2232-Novyi-metod-polucheniia-nesootvetstvii-po-tovaram/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `skus` — array[string<int64>] **обязательный**. Список идентификаторов товаров в системе Ozon — SKU.

## Ответы

**200** — Несоответствия характеристик

- `result` — array[object]. Информация о несоответствиях товаров.
  - `has_mismatches` — boolean. `true`, если в характеристиках товара есть несоответствия.
  - `mismatches` — array[object]. Список несоответствий.
    - `attribute_ids` — array[string<int64>]. Список идентификаторов характеристик, в которых есть несоответствия.
    - `id` — string. Идентификатор несоответствия.
    - `mismatch_text` — string. Описание несоответствия.
  - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.

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
