---
title: "Возвращаем доступные пункты приема подходящие по габаритным группам, у которых есть хотя бы один таймслот раньше чем самая ранняя дата \"доставить до\", с оставшейся емкостью больше чем кол-во заказов в списке"
api: uzum-seller
method: GET
path: /v1/fbs/invoice/dop/drop-off-points
operation_id: getFbsInvoiceDropOffPoints
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 30feddf4aa174b3c
---

# Возвращаем доступные пункты приема подходящие по габаритным группам, у которых есть хотя бы один таймслот раньше чем самая ранняя дата "доставить до", с оставшейся емкостью больше чем кол-во заказов в списке

`GET /v1/fbs/invoice/dop/drop-off-points`

Нужен API-ключ в заголовке Authorization, без Bearer. В Swagger UI нажмите **Authorize**.

Возвращаем доступные пункты приема подходящие по габаритным группам, у которых есть хотя бы один таймслот раньше чем самая ранняя дата "доставить до", с оставшейся емкостью больше чем кол-во заказов в списке

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `customerOrderIds` | query | array[integer<int64>] | да | — |
| `Accept-Language` | header | string (ru, uz) | нет | Язык локализации. Поддерживаемые языки: ru, uz. По умолчанию: uz |

## Ответы

**200** — Success

- `payload` — object. Подходящие пункты приема
  - `dropOffPoints` — array[object]. Список пунктов приема
    - `dimensionalGroupIsLarge` — boolean. Признак, что габаритная группа является крупной
    - `workingHours` — object. Часы работы пункта приема для каждого дня недели (ключ — день недели)
    - `latitude` — number<double>. Широта пункта приема
    - `longitude` — number<double>. Долгота пункта приема
    - `uuid` — string<uuid>. Идентификатор пункта приема
    - `address` — string. Адрес пункта приема
    - `type` — string (UNKNOWN, STOCK, ISSUE_POINT, UZ_POST, UCELL, NOT_UZUM, PHOTO_STUDIO, CROSS_DOCK, DROP_OFF_POINT, SORT_CENTER, FRANCHISE). Тип пункта доставки
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**401** — Заголовок Authorization отсутствует или пуст. Передайте Authorization: API_TOKEN без префикса Bearer; заголовок token не используется.

**403** — Ключ не найден, истёк, выключен, не даёт доступа к магазину или изменениям. Если метод требует shopIds, проверьте наличие этого параметра и доступ ко всем указанным магазинам. Значение Authorization передавайте без Bearer.
