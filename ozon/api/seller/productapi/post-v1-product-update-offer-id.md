---
title: Изменить артикулы товаров из системы продавца
api: ozon-seller
method: POST
path: /v1/product/update/offer-id
operation_id: ProductAPI_ProductUpdateOfferID
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 716643ba42d94ced
---

# Изменить артикулы товаров из системы продавца

`POST /v1/product/update/offer-id`

Метод для изменения `offer_id`, привязанных к товарам. Вы можете изменить несколько `offer_id`. Если `offer_id` уже используется для другого товара, вернётся ошибка `OFFER_ID_ALREADY_EXISTS`.

 [Подробнее о требованиях к артикулам в Базе знаний продавца](https://seller-edu.ozon.ru/libra/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/articyl-tovara#какие-есть-требования-к-артикулу)

У метода есть лимит на количество операций c товарами в минуту. Если вы превысите лимит, вернётся ошибка `429` с описанием в поле `message` и заголовками:
- `Item-Retry-After` — время в минутах до обновления лимита. Для суточного лимита — время до 03:00 по московскому времени.
- `Item-Rate-Limit-Remaining` — остаток операций до следующего сброса лимита.

Чтобы узнать лимит, используйте [/v4/product/info/limit](#operation/ProductAPI_GetUploadQuota).

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `update_offer_id` — ? **обязательный**. Список пар с новыми и старыми значениями артикулов.
  - `new_offer_id` — string **обязательный**. Новый артикул.
  - `offer_id` — string **обязательный**. Старый артикул.

## Ответы

**200** — Информация об изменении артикулов

- `errors` — ?. Список ошибок.
  - `message` — string. Сообщение об ошибке.
  - `offer_id` — string. Артикул товара, который не получилось изменить.

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

**429** — Слишком много запросов

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
