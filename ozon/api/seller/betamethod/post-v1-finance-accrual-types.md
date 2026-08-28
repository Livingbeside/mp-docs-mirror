---
title: Получить справочник начислений
api: ozon-seller
method: POST
path: /v1/finance/accrual/types
operation_id: GetFinanceAccrualTypes
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 262b7ef26b0ea25e
---

# Получить справочник начислений

`POST /v1/finance/accrual/types`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2008-Novye-beta-metody-dlia-polucheniia-nachislenii/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Справочник начислений

- `accrual_types` — array[object]. Информация о начислениях.
  - `description` — string. Описание начисления.
  - `id` — integer<int32>. Идентификатор начисления.
  - `name` — string. Название начисления.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
