---
title: Создать акцию с механикой «Скидка»
api: ozon-seller
method: POST
path: /v1/seller-actions/create/discount
operation_id: SellerActionsCreateDiscount
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fecfeb160d95c81a
---

# Создать акцию с механикой «Скидка»

`POST /v1/seller-actions/create/discount`

Недоступен для продавцов из СНГ.

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_end` — string<date-time> **обязательный**. Дата и время окончания акции.
- `date_start` — string<date-time> **обязательный**. Дата и время начала акции.
- `min_action_percent` — number<double> **обязательный**. Минимальный процент скидки.
- `title` — string. Название акции.

## Ответы

**200** — Акция создана

- `action_id` — integer<uint64>. Идентификатор акции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
