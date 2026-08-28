---
title: Получить список акций
api: ozon-seller
method: POST
path: /v1/seller-actions/list
operation_id: SellerActionsList
tags:
  - SellerActions
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: d33a1c1a5487e860
---

# Получить список акций

`POST /v1/seller-actions/list`

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1872-Novye-metody-dlia-raboty-s-aktsiiami-sellera) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `action_ids` — array[string<uint64>]. Идентификаторы акций.
- `action_type` — array[string (DISCOUNT, VOUCHER_DISCOUNT, DISCOUNT_WITH_CONDITION, INSTALLMENT, INDIVIDUAL_DISCOUNT_BY_PRODUCTS, OZON_ACCOUNT_DISCOUNT, MULTI_LEVEL_DISCOUNT_ON_AMOUNT)]. Механика акции: - `DISCOUNT` — скидка; - `VOUCHER_DISCOUNT` — скидка по промокоду; - `DISCOUNT_WITH_CONDITION` — скидка от суммы заказа; - `INSTALLMENT` — беспроцентная рассрочка; - `INDIVIDUAL_DISCOUNT_BY_PRODUCTS` — бонусы продавца; - `OZON_ACCOUNT_DISCOUNT` — повышенная скидка с картой Ozon Банка; - `MULTI_LEVEL_DISCOUNT_ON_AMOUNT` — многоуровневая скидка от суммы.
- `limit` — integer<uint64> **обязательный**. Количество значений на странице.
- `offset` — integer<uint64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента.
- `search` — string. Поиск по названию акции.
- `status` — array[string (ACTIVE, ENDED, PLANNED, PAUSED)]. Статус акции: - `ACTIVE` — активна; - `ENDED` — завершена; - `PLANNED` — запланирована; - `PAUSED` — приостановлена.

## Ответы

**200** — Список акций

- `actions` — array[object]. Список акций.
  - `action_id` — integer<uint64>. Идентификатор акции.
  - `action_parameters` — object. Параметры акции.
    - `addresses` — array[string]. Список адресов.
    - `auto_stop_action_reason` — string (UNSPECIFIED, BUDGET_EXCEEDED, FAST_BUDGET_SPENDING, BUDGET_SPENDING_IS_CRAZY). Причина остановки акции: - `UNSPECIFIED` — не определена; - `BUDGET_EXCEEDED` — закончился бюджет; - `FAST_BUDGET_SPENDING` — быстрый расход бюджета в первые часы; - `BUDGET_SPENDING_IS_CRAZY` — быстрый расход бюджета за короткое время. По умолчанию: `UNSPECIFIED`.
    - `budget` — number<double>. Бюджет акции. Если бюджет закончится, акция остановится.
    - `budget_spent` — number<double>. Расходы бюджета акции.
    - `date_end` — string<date-time>. Дата и время окончания акции.
    - `date_start` — string<date-time>. Дата и время начала акции.
    - `discount_levels` — array[object]. Уровни скидки.
      - `discount_value` — number<double>. Значение скидки.
      - `order_amount` — number<double>. Сумма заказа.
    - `discount_type` — string (UNSPECIFIED, RUB, PERCENT, FINAL_PRICE, INSTALLED_PERIOD, CURRENCY). Тип скидки: - `UNSPECIFIED` — не определён; - `RUB` — скидка в рублях; - `PERCENT` — скидка в процентах; - `FINAL_PRICE` — финальная цена; - `INSTALLED_PERIOD` — период рассрочки; - `CURRENCY` — скидка в валюте. По умолчанию: `UNSPECIFIED`.
    - `discount_value` — number<float>. Размер скидки. Если механика акции «Беспроцентная рассрочка», вернётся период рассрочки.
    - `is_legal_entities_segment` — boolean. `true`, если акция для юридических лиц.
    - `min_action_percent` — number<float>. Минимальный процент скидки.
    - `min_order_amount` — number<double>. Сумма заказа, с которой действует скидка.
    - `picked_segments` — array[object]. Список сегментов аудиторий.
      - `segments` — array[object]. Параметры сегментов аудиторий.
        - `description` — string. Описание сегмента.
        - `id` — integer<uint64>. Идентификатор сегмента.
        - `name` — string. Название сегмента.
        - `type` — string (UNSPECIFIED, OZON, SELLER). Тип сегмента: - `UNSPECIFIED` — не определён; - `OZON` — Ozon; - `SELLER` — продавца. По умолчанию: `UNSPECIFIED`.
    - `status` — string (ACTIVE, ENDED, PLANNED, PAUSED). Статус акции: - `ACTIVE` — активна; - `ENDED` — завершена; - `PLANNED` — запланирована; - `PAUSED` — приостановлена.
    - `title` — string. Название акции.
    - `type` — string (DISCOUNT, VOUCHER_DISCOUNT, DISCOUNT_WITH_CONDITION, INSTALLMENT, INDIVIDUAL_DISCOUNT_BY_PRODUCTS, OZON_ACCOUNT_DISCOUNT, MULTI_LEVEL_DISCOUNT_ON_AMOUNT). Механика акции: - `DISCOUNT` — скидка; - `VOUCHER_DISCOUNT` — скидка по промокоду; - `DISCOUNT_WITH_CONDITION` — скидка от суммы заказа; - `INSTALLMENT` — беспроцентная рассрочка; - `INDIVIDUAL_DISCOUNT_BY_PRODUCTS` — бонусы продавца; - `OZON_ACCOUNT_DISCOUNT` — повышенная скидка с картой Ozon Банка; - `MULTI_LEVEL_DISCOUNT_ON_AMOUNT` — многоуровневая скидка от суммы.
    - `voucher_parameters` — object. Параметры промокодов.
      - `count_codes` — integer<uint64>. Коды промокодов.
      - `is_private` — boolean. `true`, если промокод не в открытом доступе.
      - `type` — string (UNSPECIFIED, ONE, MULTIPLE, UNIQUE). Тип промокода: - `UNSPECIFIED` — не определён; - `ONE` — промокод для всех покупателей на 1 заказ; - `MULTIPLE` — промокод для всех покупателей на любое количество заказов; - `UNIQUE` — промокод для 1 покупателя на 1 заказ. По умолчанию: `UNSPECIFIED`.
    - `warehouses` — array[string<uint64>]. Список складов.
  - `allow_delete` — boolean. `true`, если акцию можно удалить.
  - `highlight_url` — string. Ссылка на хайлайт.
  - `is_editable` — boolean. `true`, если акцию можно редактировать.
  - `is_participated` — boolean. `true`, если в акцию был добавлен хотя бы 1 товар.
  - `is_turn_on` — boolean. `true`, если акция включена.
  - `sku_count` — integer<uint64>. Общее количество товаров в акции.
- `total` — integer<uint64>. Общее количество акций.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
