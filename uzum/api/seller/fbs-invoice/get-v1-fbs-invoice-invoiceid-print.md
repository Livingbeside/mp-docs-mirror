---
title: Печать акта поставки
api: uzum-seller
method: GET
path: /v1/fbs/invoice/{invoiceId}/print
operation_id: printFbsInvoice
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: d1bafd60d907e789
---

# Печать акта поставки

`GET /v1/fbs/invoice/{invoiceId}/print`

Нужен API-ключ в заголовке Authorization, без Bearer. В Swagger UI нажмите **Authorize**.

Печать акта поставки

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `invoiceId` | path | integer<int64> | да | Идентификатор акта поставки |

## Ответы

**200** — OK

- `payload` — object. Document
  - `document` — string<byte> **обязательный**. Накладная в pdf в Base64
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
