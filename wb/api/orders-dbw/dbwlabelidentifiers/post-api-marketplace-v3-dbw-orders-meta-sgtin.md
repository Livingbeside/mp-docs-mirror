---
title: Закрепить коды маркировки Честного знака за сборочными заданиями
api: wb-orders-dbw
method: POST
path: /api/marketplace/v3/dbw/orders/meta/sgtin
operation_id: postV3DbwOrdersMetaSgtin
tags:
  - dbwLabelIdentifiers
spec_version: ordersdbw
source: "https://dev.wildberries.ru/docs/openapi/orders-dbw"
deprecated: false
content_sha: b7808b8883c39418
---

# Закрепить коды маркировки Честного знака за сборочными заданиями

`POST /api/marketplace/v3/dbw/orders/meta/sgtin`

Описание метода

Метод обновляет код маркировки [Честного знака](https://честныйзнак.рф/) в [идентификаторах маркировки сборочных заданий](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails).

Закрепить код маркировки можно только за сборочным заданием в [статусе](./orders-dbw#tag/dbwAssemblyOrders/operation/postV3DbwOrdersStatus) `confirm` и если в [идентификаторах маркировки сборочного задания](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails) есть поле `sgtin`.

Получить загруженные маркировки можно в [идентификаторах маркировки сборочного задания](./orders-dbw#tag/dbwLabelIdentifiers/operation/postV3DbwOrdersMetaDetails).

Лимит запросов на один аккаунт продавца для следующих методов DBW:

 получение и обновление списка контактов

 получение и удаление идентификаторов маркировки

 методы сборочных заданий

 

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[object] **обязательный**
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `sgtins` — array[string] **обязательный**. Массив кодов маркировки. Допускается от 16 до 135 символов для кода одной маркировки

## Ответы

**200** — Успешно

- `requestId` — string. Уникальный ID запроса, содержащего ошибки.
- `results` — array[object] **обязательный**
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки: - `404` - `409`
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено - `StatusMismatch` — операция невозможна для этого статуса сборочного задания - `ImeiIsNotFilled` — не заполнен IMEI - `MetaValidationFail` — ошибки валидации идентификаторов маркировки
    - `metaDetails` — array[object]. Детали ошибки валидации идентификаторов маркировки
      - `key` — string **обязательный**. Идентификатор маркировки
      - `value` — string. Значение идентификатора маркировки
      - `decision` — string **обязательный**. Статус проверки: - `sgtin` - `sgtinInvalidFormat` — Неверный формат маркировки - `sgtinNotFound` — Маркировка не найдена в [Честном знаке](https://chestnyznak.ru) - `sgtinEmitted` — Маркировка эмитирована - `sgtinApplied` — Не пройдена процедура Ввод в оборот - `sgtinWrittenOff` — Списан - `sgtinRetired` — Выбыл - `sgtinWithdrawn` — Выбыл - `sgtinDisaggregation` — Расформирован - `sgtinDisaggregated` — Расформирован - `sgtinAppliedNotPaid` — Не оплачен - `pending` — Маркировка на проверке
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `orderId` — integer **обязательный**. ID сборочного задания с успешно обновлёнными данными

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

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

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
