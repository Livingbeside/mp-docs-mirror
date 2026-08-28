---
title: Проверить код курьера
api: ozon-seller
method: POST
path: /v1/posting/fbs/pick-up-code/verify
operation_id: PostingAPI_PostingFBSPickupCodeVerify
tags:
  - FBS
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: ffc4e0f22293a7a7
---

# Проверить код курьера

`POST /v1/posting/fbs/pick-up-code/verify`

Метод позволяет проверить код курьера при передаче отправлений realFBS Express. Подробнее о передаче отправлений в [Базе знаний продавца](https://seller-edu.ozon.ru/contract-for-sellers/regulations-fbs-realfbs/reglament-prodaji-so-svoego-sklada-fbs-express#7-порядок-передачи-отправлении-через-партнёров-ozon-при-экспресс-доставке).

## Запрос

**Тело запроса** (`application/json`):

- `pickup_code` — string **обязательный**. Код курьера.
- `posting_number` — string **обязательный**. Номер отправления.

## Ответы

**200** — Результат проверки

- `valid` — boolean. `true`, если код корректный.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
