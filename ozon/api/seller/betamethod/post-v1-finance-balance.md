---
title: Получить отчёт о балансе
api: ozon-seller
method: POST
path: /v1/finance/balance
operation_id: GetFinanceBalanceV1
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fe623f862c17d1cf
---

# Получить отчёт о балансе

`POST /v1/finance/balance`

Соответствует разделу **Финансы → Баланс** в личном кабинете.

Вы можете оставить обратную связь по этому методу в комментариях к [обсуждению](https://dev.ozon.ru/community/1732-Novyi-metod-polucheniia-dannykh-po-balansu/) в сообществе разработчиков Ozon for dev.

## Запрос

**Тело запроса** (`application/json`):

- `date_from` — string<date-time> **обязательный**. Дата начала отчётного периода в формате `YYYY-MM-DD`.
- `date_to` — string<date-time> **обязательный**. Дата окончания отчётного периода в формате `YYYY-MM-DD`. Максимальный период между `date_from` и `date_to` — 30 дней.

## Ответы

**200** — Отчёт о балансе

- `cashflows` — object. Информация о доходах и расходах.
  - `returns` — object. Начисления за возвраты.
    - `amount` — object. Сумма возвратов.
      - `currency_code` — string. Валюта.
      - `value` — number<double>. Сумма.
    - `amount_details` — object. Детализация суммы возвратов.
      - `partner_programs` — object. Выплаты по механикам лояльности партнёров.
        - `currency_code` — string. Валюта.
        - `value` — number<double>. Сумма.
      - `points_for_discounts` — string. Баллы за скидки.
      - `revenue` — object. Сумма, которую оплатили покупатели.
        - `currency_code` — string. Валюта.
        - `value` — number<double>. Сумма.
    - `fee` — object. Сумма вознаграждения Ozon.
      - `currency_code` — string. Валюта.
      - `value` — number<double>. Сумма.
  - `sales` — object. Начисления за продажи.
    - `amount` — object. Сумма продаж.
      - `currency_code` — string. Валюта.
      - `value` — number<double>. Сумма.
    - `amount_details` — object. Детализация суммы продаж.
      - `partner_programs` — object. Выплаты по механикам лояльности партнёров.
        - `currency_code` — string. Валюта.
        - `value` — number<double>. Сумма.
      - `points_for_discounts` — string. Баллы за скидки.
      - `revenue` — object. Сумма, которую оплатили покупатели.
        - `currency_code` — string. Валюта.
        - `value` — number<double>. Сумма.
    - `fee` — object. Сумма вознаграждения Ozon.
      - `currency_code` — string. Валюта.
      - `value` — number<double>. Сумма.
  - `services` — array[object]. Начисления за другие услуги.
    - `amount` — object. Сумма начислений за другие услуги.
      - `currency_code` — string. Валюта.
      - `value` — number<double>. Сумма.
    - `name` — string. Cистемное название услуги.
- `total` — object. Общие данные по балансу за период.
  - `accrued` — object. Начислено за период.
    - `currency_code` — string. Валюта.
    - `value` — number<double>. Сумма.
  - `closing_balance` — object. Баланс на конец периода.
    - `currency_code` — string. Валюта.
    - `value` — number<double>. Сумма.
  - `opening_balance` — object. Баланс на начало периода.
    - `currency_code` — string. Валюта.
    - `value` — number<double>. Сумма.
  - `payments` — array[object]. Выплаты за период.
    - `currency_code` — string. Валюта.
    - `value` — number<double>. Сумма.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
