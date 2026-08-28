---
title: Получить идентификаторы маркировки сборочных заданий{{ /api/marketplace/v3/click-collect/orders/meta/details }}
api: wb-in-store-pickup
method: POST
path: /api/marketplace/v3/click-collect/orders/meta/details
operation_id: postV3ClickCollectOrdersMetaDetails
tags:
  - inStorePickupLabelIdentifiers
spec_version: instorepickup
source: "https://dev.wildberries.ru/docs/openapi/in-store-pickup"
deprecated: false
content_sha: c7e98423145eb343
---

# Получить идентификаторы маркировки сборочных заданий{{ /api/marketplace/v3/click-collect/orders/meta/details }}

`POST /api/marketplace/v3/click-collect/orders/meta/details`

Описание метода Метод возвращает идентификаторы маркировки [сборочных заданий ](./in-store-pickup#tag/inStorePickupAssemblyOrders) и статусы их проверки. Перечень идентификаторов маркировки, доступных для сборочного задания, можно получить в [списке новых сборочных заданий](./in-store-pickup#tag/inStorePickupAssemblyOrders/operation/getV3ClickCollectOrdersNew), поле `requiredMeta`. Если поле `requiredMeta` не содержит какой-либо идентификатор маркировки, значит, у сборочного задания не может быть этого идентификатора — и добавить его нельзя. Возможные идентификаторы маркировки: - `imei` — [IMEI](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaImei) - `uin` — [УИН](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaUin) - `gtin` — [GTIN](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaGtin) - `sgtin` — [код маркировки](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaSgtin) - `customsDeclaration` — [номер ДТ](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaCustomsDeclaration) - `originCountryCode` — [числовой код страны происхождения товара](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaCustomsDeclaration) из [Общероссийского классификатора стран мира](https://esnsi.gosuslugi.ru/classifiers/16269) Лимит запросов на один аккаунт продавца для всех методов получения и удаления идентификаторов маркировки Самовывоз : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 150 запросов | 400 мс | 20 запросов | Один запрос с кодами ответов 4XX учитывается как 10 запросов

## Запрос

**Тело запроса** (`application/json`):

- `ordersIds` — array[integer] **обязательный**. Список ID сборочных заданий

## Ответы

**200** — Успешно

- `requestId` — string **обязательный**. Уникальный ID запроса
- `orders` — array[object] **обязательный**. Идентификаторы маркировки сборочных заданий и статусы их валидации
  - `orderId` — integer **обязательный**. ID сборочного задания
  - `isError` — boolean **обязательный**. Есть ли ошибки
  - `errors` — array[object]. Информация об ошибке
    - `code` — integer **обязательный**. Код ошибки
    - `detail` — string **обязательный**. Дополнительная информация об ошибке
  - `metaDetails` — array[object] **обязательный**. Идентификаторы маркировки и статусы их валидации
    - `key` — string **обязательный**. Идентификатор маркировки: - `imei` — [IMEI](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaImei) - `uin` — [УИН](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaUin) - `gtin` — [GTIN](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaGtin) - `sgtin` — [код маркировки](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaSgtin) - `customsDeclaration` — [номер ДТ](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaCustomsDeclaration) - `originCountryCode` — [числовой код страны происхождения товара](./in-store-pickup#tag/inStorePickupLabelIdentifiers/operation/postV3ClickCollectOrdersMetaCustomsDeclaration) из [Общероссийского классификатора стран мира](https://esnsi.gosuslugi.ru/classifiers/16269)
    - `value` — string. Значение идентификатора маркировки
    - `decision` — string **обязательный**. Статусы проверки идентификатора маркировки. - `imei` - `filled` — Маркировка закреплена за сборочным заданием, проверка не требуется - `optional` — Маркировка не закреплена за сборочным заданием и не обязательна. Проверка пройдена - `deadlineExceeded` — Проверка маркировки не завершена и будет продолжена. Проверка может завершиться и успешно, и неуспешно - `imeiMaySell` — Товар допущен к продаже. Проверка пройдена - `imeiSoldB2B` — Товар продан покупателю B2B, допущен к продаже повторно. Проверка пройдена - `pending` — Проверка маркировки продолжается. Дождитесь изменения статуса проверки - `required` — Маркировка обязательна и не закреплена за сборочным заданием. Проверка не пройдена - `imeiInvalidFormat` — Указан неверный формат маркировки. Проверка не пройдена - `imeiAlreadySold` — Товар с этим IMEI уже продан. Проверка не пройдена - `uin` - `filled` — Маркировка закреплена за сборочным заданием, проверка не требуется - `optional` — Маркировка не закреплена за сборочным заданием и не обязательна. Проверка пройдена - `required` — Маркировка обязательна и не закреплена за сборочным заданием. Проверка не пройдена - `sgtin` - `filled` — Маркировка закреплена за сборочным заданием, проверка не требуется - `optional` — Маркировка не закреплена за сборочным заданием и не обязательна. Проверка пройдена - `deadlineExceeded` — Проверка маркировки не завершена и будет продолжена. Проверка может завершиться и успешно, и неуспешно - `sgtinIntroduced` — Товар допущен к продаже. Проверка пройдена - `sgtinSoldB2B` — Товар продан покупателю B2B, допущен к продаже повторно. Проверка пройдена - `pending` — Проверка маркировки продолжается. Дождитесь изменения статуса проверки - `required` — Маркировка обязательна и не закреплена за сборочным заданием. Проверка не пройдена - `sgtinInvalidFormat` — Указан неверный формат маркировки. Проверка не пройдена - `sgtinNotFound` — Маркировка не найдена в [Честном знаке](https://chestnyznak.ru). Проверка не пройдена - `sgtinEmitted` — Маркировка эмитирована. Проверка не пройдена - `sgtinApplied` — Не пройдена процедура Ввод в оборот. Проверка не пройдена - `sgtinWrittenOff` — Списан. Проверка не пройдена - `sgtinRetired` — Выбыл. Проверка не пройдена - `sgtinWithdrawn` — Выбыл. Проверка не пройдена - `sgtinDisaggregated` — Расформирован. Проверка не пройдена - `sgtinDisaggregation` — Расформирован. Проверка не пройдена - `sgtinAppliedNotPaid` — Не оплачен. Проверка не пройдена - `gtin` - `filled` — Маркировка закреплена за сборочным заданием, проверка не требуется - `optional` — Маркировка не закреплена за сборочным заданием и не обязательна. Проверка пройдена - `required` — Маркировка обязательна и не закреплена за сборочным заданием. Проверка не пройдена - `customsDeclaration` - `filled` — Маркировка закреплена за сборочным заданием, проверка не требуется - `optional` — Маркировка не закреплена за сборочным заданием и не обязательна. Проверка пройдена - `required` — Маркировка обязательна и не закреплена за сборочным заданием. Проверка не пройдена

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
