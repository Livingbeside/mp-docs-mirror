---
title: Обновить акцию с механикой «Скидка по промокоду»
api: ozon-seller
method: POST
path: /v1/seller-actions/update/voucher
operation_id: SellerActionsUpdateVoucher
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d3f1f68eaf8470b8
---

# Обновить акцию с механикой «Скидка по промокоду»

`POST /v1/seller-actions/update/voucher`

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_id` — integer<uint64>. Идентификатор акции. Получите значение параметра методом [/v1/seller-actions/list](#operation/SellerActionsList).
- `action_parameters` — object. Параметры акции.
  - `budget` — integer<int64> **обязательный**. Бюджет акции. Перед тем как его изменить, выключите акцию методом [/v1/seller-actions/change-activity](#operation/SellerActionsChangeActivity).
  - `date_end` — string<date-time> **обязательный**. Дата и время окончания акции.
  - `date_start` — string<date-time> **обязательный**. Дата и время начала акции.
  - `discount_value` — number<double> **обязательный**. Размер скидки.
  - `title` — string **обязательный**. Название акции.
  - `user_ids` — array[string<uint64>]. Идентификаторы пользователей, которым доступен промокод.

## Ответы

**200** — Акция обновлена

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
