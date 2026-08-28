---
title: Создать акцию с механикой «Беспроцентная рассрочка»
api: ozon-seller
method: POST
path: /v1/seller-actions/create/installment
operation_id: SellerActionsCreateInstallment
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 59e55af8b915d6b6
---

# Создать акцию с механикой «Беспроцентная рассрочка»

`POST /v1/seller-actions/create/installment`

Период рассрочки — 6 месяцев. Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `date_start` — string<date-time> **обязательный**. Дата и время начала акции.
- `title` — string **обязательный**. Название акции.

## Ответы

**200** — Акция создана

- `action_id` — integer<uint64>. Идентификатор акции.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
