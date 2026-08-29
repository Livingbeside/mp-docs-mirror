---
title: Создание, изменение и удаление ответа или комментария
api: yandex-market
method: POST
path: /v1/businesses/{businessId}/goods-questions/update
operation_id: updateGoodsQuestionTextEntity
tags:
  - goods-questions
  - fby
  - fbs
  - dbs
  - express
spec_version: LATEST
source: "https://yandex.ru/dev/market/partner-api/"
deprecated: false
content_sha: 8da42dc7706cb2f0
---

# Создание, изменение и удаление ответа или комментария

`POST /v1/businesses/{businessId}/goods-questions/update`

{% include notitle [access](../../_auto/method_scopes/updateGoodsQuestionTextEntity.md) %}

Создание, изменение и удаление ответа или комментария.

{% include notitle [limit](../../_auto/method_limits/updateGoodsQuestionTextEntity.md) %}

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `businessId` | path | integer<int64> | да | Идентификатор кабинета. {% if audience == "partner" %} Чтобы его узнать, воспользуйтесь запросом [GET v2/campaigns](../../reference/campaigns/getCampaigns.md). ℹ️ [Что такое кабинет и магазин на Маркете](https://yandex.ru/support/marketplace/account/introduction.html) {% endif %} |

## Запрос

**Тело запроса** (`application/json`):

- `entityId` — object. Идентификатор обновляемого или удаляемого ответа или комментария. Обязателен для операций `UPDATE` и `DELETE`.
  - `id` — integer<int64> **обязательный**. Идентификатор вопроса, ответа или комментария.
  - `type` — string (QUESTION, ANSWER, COMMENT) **обязательный**. Тип сущности (вопрос, ответ или комментарий).
- `parentEntityId` — object. Идентификатор родительского вопроса или ответа. Обязателен для операции `CREATE`. Используется для создания ответа или комментария: * При создании ответа — указывайте идентификатор вопроса. * При создании комментария к ответу — указывайте идентификатор ответа.
  - `id` — integer<int64> **обязательный**. Идентификатор вопроса, ответа или комментария.
  - `type` — string (QUESTION, ANSWER, COMMENT) **обязательный**. Тип сущности (вопрос, ответ или комментарий).
- `text` — string. Текст ответа или комментария. Обязателен для операций `CREATE` и `UPDATE`. Не требуется для операции `DELETE`.
- `operationType` — string (UPDATE, CREATE, DELETE) **обязательный**. Операция над ответом или комментарием. * `UPDATE` — обновление. * `CREATE` — создание. * `DELETE` — удаление.

## Ответы

**200** — Информация о созданном ответе или комментарии. Возвращается только при операции создания (`operationType` = `CREATE`). При обновлении и удалении возвращается пустой ответ.

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `result` — object. Информация о созданном ответе или комментария. Возвращается только для запроса создания.
  - `entity` — object **обязательный**. Идентификатор вопроса, ответа или комментария.
    - `id` — integer<int64> **обязательный**. Идентификатор вопроса, ответа или комментария.
    - `type` — string (QUESTION, ANSWER, COMMENT) **обязательный**. Тип сущности (вопрос, ответ или комментарий).

**400** — Запрос содержит неправильные данные. [Подробнее об ошибке](../../concepts/error-codes.md#questions)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**401** — В запросе не указаны данные для авторизации. [Подробнее об ошибке](../../concepts/error-codes.md#401)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**403** — Данные для авторизации неверны или доступ к ресурсу запрещен. [Подробнее об ошибке](../../concepts/error-codes.md#403)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**404** — Запрашиваемый ресурс не найден. [Подробнее об ошибке](../../concepts/error-codes.md#404)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**420** — Превышено ограничение на доступ к ресурсу. [Подробнее об ошибке](../../concepts/error-codes.md#420)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.

**500** — Внутренняя ошибка Маркета. [Подробнее об ошибке](../../concepts/error-codes.md#500)

- `status` — string (OK, ERROR) **обязательный**. Тип ответа. Возможные значения: * `OK` — ошибок нет. * `ERROR` — при обработке запроса произошла ошибка.
- `errors` — array[object]. Список ошибок.
  - `code` — string **обязательный**. Код ошибки.
  - `message` — string. Описание ошибки.
