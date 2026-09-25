---
title: Установить ID ЭТрН поставок
api: wb-orders-fbs
method: PATCH
path: /api/marketplace/v3/fbs/supplies/waybill
operation_id: patchV3FbsSuppliesWaybill
tags:
  - fbsSupplies
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 1ed7063cddbef8d9
---

# Установить ID ЭТрН поставок

`PATCH /api/marketplace/v3/fbs/supplies/waybill`

Описание метода

Метод устанавливает ID ЭТрН — электронной транспортной накладной. Чтобы использовать метод, укажите [место отгрузки поставки](./orders-fbs#tag/fbsSupplies/operation/patchV3FbsSuppliesShippingMethod) со способом доставки `"shippingType":"transportCompany"`.

ID ЭТрН нужно указать до передачи поставки в доставку. Вы можете обновлять ID ЭТрН до сканирования поставки и её коробов в пункте отгрузки. Когда поставка будет отсканирована, метод начнёт возвращать ошибку `409`.

В запросе можно указать максимум 100 поставок. Результат обработки возвращается для каждой поставки отдельно.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `data` — array[object] **обязательный**
  - `supplyId` — string **обязательный**. ID поставки
  - `waybillUuid` — string<uuid> **обязательный**. ID ЭТрН

## Ответы

**200** — Успешно

- `results` — array[object] **обязательный**
  - `error` — object. Ошибка обработки запроса для поставки. Возможные варианты ошибок: - `400 IncorrectRequestBody`: - некорректный ID поставки - склад назначения находится не в РФ - `404 NotFound` — поставка не найдена - `409 SupplyAlreadyScanned` — поставка или её короба уже отсканированы в пункте отгрузки - `409 SupplyShippingRequired` — не указан пункт отгрузки поставки - `409 UnsuitableShippingType` — не указан способ доставки либо способ доставки не `transportCompany` - `409 WaybillUUIDIsProcessing` — ЭТрН находится в обработке
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. Дополнительная информация об ошибке
  - `success` — boolean. Успешна ли обработка запроса для данной поставки. Может быть только `true`
  - `supplyId` — string **обязательный**. ID поставки

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

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

- `code` — string. Код ошибки
- `message` — string. Описание ошибки
- `data` — object. Дополнительные данные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
