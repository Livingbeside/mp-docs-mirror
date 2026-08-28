---
title: Проверить возможность получения возвратных отгрузок по штрихкоду
api: ozon-seller
method: POST
path: /v1/return/giveout/is-enabled
operation_id: ReturnAPI_GiveoutIsEnabled
tags:
  - ReturnAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 31fe419d4caec8bb
---

# Проверить возможность получения возвратных отгрузок по штрихкоду

`POST /v1/return/giveout/is-enabled`

Если у вас есть доступ, в параметре `enabled` будет указано значение `true`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- _(схема не детализирована, см. spec.json)_

## Ответы

**200** — Результат проверки

- `enabled` — boolean. `true`, если вы можете получить возвратную отгрузку по штрихкоду.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
