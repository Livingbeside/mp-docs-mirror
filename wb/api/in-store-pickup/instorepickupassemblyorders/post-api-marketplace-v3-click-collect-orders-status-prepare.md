---
title: Сообщить, что сборочные задания готовы к выдаче
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/status/prepare
operation_id: postV3ClickCollectOrdersStatusPrepare
tags:
  - inStorePickupAssemblyOrders
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: bfb90b83f8f1fb2e
---

# Сообщить, что сборочные задания готовы к выдаче

`POST /api/marketplace/v3/click-collect/orders/status/prepare`

Описание метода

Метод переводит [сборочные задания](./in-store-pickup#tag/inStorePickupAssemblyOrders) из [статуса](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/postV3ClickCollectOrdersStatusInfo) `confirm` — на сборке — в статус `prepare` — готово к выдаче.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 сек | 1 запрос | 1 сек | 10 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — ? **обязательный**. Уникальный ID запроса
- `results` — ? **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `MetaValidationFail` — идентификаторы маркировки не прошли проверку
    - `metaDetails` — array[object]
      - `decision` — string. Ошибки проверки идентификаторов маркировки. - `imei` - `pending` — Проверка маркировки продолжается. Дождитесь изменения статуса проверки - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `imeiInvalidFormat` — Указан неверный формат маркировки - `imeiAlreadySold` — Товар с этим IMEI уже продан - `uin` - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `sgtin` - `pending` — Проверка маркировки продолжается. Дождитесь изменения статуса проверки - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `sgtinInvalidFormat` — Указан неверный формат маркировки - `sgtinNotFound` — Маркировка не найдена в [Честном знаке](https://chestnyznak.ru) - `sgtinEmitted` — Маркировка эмитирована - `sgtinApplied` — Не пройдена процедура Ввод в оборот - `sgtinWrittenOff` — Списан - `sgtinRetired` — Выбыл - `sgtinWithdrawn` — Выбыл - `sgtinDisaggregated` — Расформирован - `sgtinDisaggregation` — Расформирован - `sgtinAppliedNotPaid` — Не оплачен - `gtin` - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `expiration` - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `customsDeclaration` - `required` — Маркировка обязательна и не закреплена за сборочным заданием
      - `key` — string. Идентификатор маркировки
      - `value` — string. Значение идентификатора маркировки
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `orderId` — integer **обязательный**. ID сборочного задания

**400** — Неправильный запрос

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
