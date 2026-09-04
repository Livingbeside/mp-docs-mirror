---
title: Получить данные СПОТ для списка поставок
api: wb-orders-fbs
method: POST
path: /api/marketplace/v3/fbs/supplies/spot/list
operation_id: postV3FbsSuppliesSpotList
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: dc833d9201d198a1
---

# Получить данные СПОТ для списка поставок

`POST /api/marketplace/v3/fbs/supplies/spot/list`

Описание метода

Метод возвращает данные СПОТ для списка поставок.

Вы можете получить данные СПОТ, только если выполняются все условия:
 - поставка находится на этапе доставки
 - продавец зарегистрирован в любой стране ЕАЭС кроме РФ
 - склад назначения находится в РФ

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `supplyIds` — array[string] **обязательный**. Список ID поставок

## Ответы

**200** — Успешно

- `supplies` — array[object] **обязательный**
  - `id` — string **обязательный**. ID поставки
  - `spot` — object
    - `status` — string (pending, completed, failed) **обязательный**. Статус СПОТ: - `pending` — ожидается результат формирования ДОПП — документа о предстоящей поставке - `completed` — ДОПП успешно сформирован. Можно [получить QR-код](./orders-fbs#tag/Postavki-FBS/operation/getV3FbsSuppliesSupplyIdStickersSpot) - `failed` — ошибка формирования ДОПП. Подробнее в поле `errorCode`
    - `carrierName` — string **обязательный**. Наименование перевозчика
    - `carrierTaxNumber` — string **обязательный**. ИНН перевозчика
    - `carrierCountryCode` — string **обязательный**. Код страны перевозчика по [ОКСМ](./orders-fbs#tag/Postavki-FBS/operation/getV3FbsDictionariesCountriesOksm)
    - `vehicleRegistrationNumber` — string **обязательный**. Регистрационный номер транспортного средства
    - `trailerRegistrationNumber` — string. Регистрационный номер прицепа
    - `errorCode` — string (doppFailed). Код ошибки от сервиса формирования ДОПП — документа о предстоящей поставке. Возвращается при `"status": "failed"`. Чтобы исправить ошибку, проверьте данные СПОТ и [добавьте их в поставку](./orders-fbs#tag/Postavki-FBS/operation/getV3FbsSuppliesSupplyIdSpot) ещё раз
  - `error` — object
    - `detail` — string **обязательный**. Детали ошибки
    - `title` — string **обязательный**. Заголовок ошибки

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `title` — string **обязательный**. Заголовок ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
