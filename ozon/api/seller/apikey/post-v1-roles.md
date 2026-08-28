---
title: Получить список ролей и методов по API-ключу
api: ozon-seller
method: POST
path: /v1/roles
operation_id: AccessAPI_RolesByToken
tags:
  - APIkey
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 96dbb4a20de08299
---

# Получить список ролей и методов по API-ключу

`POST /v1/roles`

Метод для получения информации и ролях и методах, привязанных к API-ключу.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Ответы

**200** — Список ролей и методов

- `expires_at` — string<date-time>. Дата истечения срока действия ключа.
- `roles` — array[object]. Информация о доступных ролях и методах.
  - `methods` — array[string]. Методы, доступные для роли.
  - `name` — string. Название роли.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
