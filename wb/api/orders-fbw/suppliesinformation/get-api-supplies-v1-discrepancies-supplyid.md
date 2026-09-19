---
title: Расхождения в поставке{{ /api/supplies/v1/discrepancies/{supplyId} }}
api: wb-orders-fbw
method: GET
path: /api/supplies/v1/discrepancies/{supplyId}
operation_id: getV1SuppliesSupplyIdDiscrepanciesQuantity
tags:
  - suppliesInformation
spec_version: ordersfbw
source: "https://dev.wildberries.ru/docs/openapi/orders-fbw"
deprecated: false
content_sha: 35997d1b871aaf9e
---

# Расхождения в поставке{{ /api/supplies/v1/discrepancies/{supplyId} }}

`GET /api/supplies/v1/discrepancies/{supplyId}`

Описание метода

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Персональному токену

Метод возвращает информацию о выявленных расхождениях между заявленным и фактическим количеством товара в поставке.

Для поставок принятых не позднее года назад.

**Типы расхождений:**

Расхождение в большую сторону:

1. Избыток товара с заявленным баркодом:
 - `"discrepancyType": "surplus"`
 - `"discrepancyLabel": "surplus"`
2. Избыток товара с несоответствующим заявленному баркодом:
 - `"discrepancyType": "surplus"`
 - `"discrepancyLabel": "re-sorting"`

Расхождение в меньшую сторону:

1. Не хватает товара:
 - `"discrepancyType": "shortage"`
 - `"discrepancyLabel": "shortage"`
2. Некоторые баркоды не соответствуют заявленным:
 - `"discrepancyType": "shortage"`
 - `"discrepancyLabel": "re-sorting"`

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string<integer> | да | ID поставки |

## Ответы

**200** — Успешно

- `packageCode` — string **обязательный**. ID упаковки
- `videoUrl` — string **обязательный**. Видео фиксации расхождений в процессе приёмки
- `videoStartsAt` — string<date-time> **обязательный**. Дата и время видеофиксации расхождений в процессе приемки
- `videoUnavailable` — boolean **обязательный**. Доступность видео: - `false` — видео доступно - `true` — видео недоступно
- `items` — array[object] **обязательный**. Товары поставки
  - `declaredSku` — string **обязательный**. Баркод, заявленный при формировании поставки
  - `discrepancyType` — string (surplus, shortage, re-sorting) **обязательный**. Тип расхождения в целом по коробу: - `surplus` — товара в коробе больше заявленного - `shortage` — товара в коробе меньше заявленного - `re-sorting` — баркод принятого товара не соответствует заявленному при формировании поставки
  - `declaredAmount` — integer **обязательный**. Количество товара, заявленное при формировании поставки
  - `actualAmount` — integer **обязательный**. Фактическое количество товара
  - `discrepancyQuantity` — integer **обязательный**. Разница между заявленным и фактическим количеством товара
  - `actualSku` — string **обязательный**. Фактический баркод
  - `skuScans` — array[object] **обязательный**. Результаты сканирования товаров
    - `scanId` — integer **обязательный**. ID сканирования
    - `declaredSku` — string **обязательный**. Баркод, заявленный при формировании поставки
    - `scanTime` — string<date-time> **обязательный**. Дата и время сканирования
    - `discrepancyLabel` — string (surplus, shortage, re-sorting) **обязательный**. Тип расхождения товара: - `surplus` — товара больше, чем заявлено - `shortage` — товара меньше, чем заявлено - `re-sorting` — баркод принятого товара не соответствует заявленному при формировании поставки
    - `actualSku` — string **обязательный**. Фактический баркод

**400** — Неправильный запрос

- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки
- `detail` — string. Описание ошибки
- `requestId` — string. ID запроса
- `origin` — string. Сервис, вернувший ошибку

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `status` — integer **обязательный**. HTTP-статус код
- `title` — string **обязательный**. Краткое описание ошибки
- `detail` — string **обязательный**. Подробное описание ошибки
- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. Сервис, в котором произошла ошибка

**404** — Не найдено

- `status` — integer. HTTP статус-код
- `title` — string. ID ошибки
- `detail` — string. Описание ошибки
- `requestId` — string. ID запроса
- `origin` — string. Сервис, вернувший ошибку

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
