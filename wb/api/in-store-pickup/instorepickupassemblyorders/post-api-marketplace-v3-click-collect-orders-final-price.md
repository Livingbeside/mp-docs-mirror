---
title: Получить цены продавца и суммы к оплате
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/final-price
operation_id: postV3ClickCollectOrdersFinalPrice
tags:
  - inStorePickupAssemblyOrders
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: 6bbab25f9161ff62
---

# Получить цены продавца и суммы к оплате

`POST /api/marketplace/v3/click-collect/orders/final-price`

Описание метода

Метод возвращает:
 - цены продавца без учёта скидок
 - суммы к оплате покупателем с учетом всех скидок и кэшбека

Лимит запросов на один аккаунт продавца для всех методов получения и удаления идентификаторов маркировки Самовывоз:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 150 запросов | 400 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Запрос

**Тело запроса** (`application/json`):

- `orders` — array[integer]. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — string **обязательный**. Уникальный ID запроса
- `results` — array[object] **обязательный**. Данные ответа
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `data` — object. Данные сборочного задания. Если `"data":{}`, данные формируются. Повторите запрос позднее. Максимальное время формирования данных около 3 минут. Если `data` отсутствует, данных по сборочному заданию не предусмотрено. Используйте данные из ответов методов: - [Получить список новых сборочных заданий](/docs/openapi/in-store-pickup#tag/inStorePickupAssemblyOrders/operation/getV3ClickCollectOrdersNew) - [Получить информацию о завершенных сборочных заданиях](/docs/openapi/in-store-pickup#tag/inStorePickupAssemblyOrders/operation/getV3ClickCollectOrders)
    - `originalPrice` — integer. Цена продавца в валюте продажи без учёта скидок, умноженная на 100. Предоставляется в информационных целях
    - `convertedOriginalPrice` — integer. Цена продавца в валюте страны продавца без учёта скидок, умноженная на 100. Предоставляется в информационных целях
    - `originalFinalPrice` — integer. Сумма к оплате покупателем в валюте продажи с учетом всех скидок и кэшбека, умноженная на 100. Код валюты продажи указан в поле `currencyCode`. Предоставляется в информационных целях
    - `convertedOriginalFinalPrice` — integer. Сумма к оплате покупателем в валюте страны продавца с учетом всех скидок и кэшбека, умноженная на 100. Предоставляется в информационных целях
    - `currencyCode` — integer<ISO 4217>. Код валюты продажи
    - `convertedCurrencyCode` — integer<ISO 4217>. Код валюты страны продавца
  - `errors` — array[object]. Детали ошибки
    - `code` — integer **обязательный**. Код ошибки: - `404` — `NotFound` - `400` — `StatusMismatch` - `422` — `PriceNotCalculated`
    - `detail` — string **обязательный**. - `NotFound` — сборочное задание не найдено (`404`) - `StatusMismatch` — операция невозможна для этого статуса сборочного задания (`400`) - `PriceNotCalculated` — операция невозможна для сборочных заданий, созданных ранее 23.07.2026 (`422`)
  - `isError` — boolean. Есть ли ошибки

**400** — Неправильный запрос

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
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

**403** — Доступ запрещён

- `detail` — object. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. Уникальный ID запроса
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
