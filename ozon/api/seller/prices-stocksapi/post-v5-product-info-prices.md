---
title: Получить информацию о цене товара
api: ozon-seller
method: POST
path: /v5/product/info/prices
operation_id: ProductAPI_GetProductInfoPrices
tags:
  - Prices&StocksAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4c94cb8cd467f347
---

# Получить информацию о цене товара

`POST /v5/product/info/prices`

23 ноября 2026 года отключим параметр total в ответе метода. Переключитесь на total_items.

Вы можете посмотреть историю обновления цен только в личном кабинете продавца.
 [Подробнее об истории обновления цен в Базе знаний продавца](https://seller-edu.ozon.ru/libra/ceny-i-akcii/rabota-s-cenami/price-control#как-посмотреть-историю-обновления-цен)

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object **обязательный**. Фильтр по товарам.
  - `offer_id` — ?. Фильтр по параметру `offer_id`. Можно передавать до 1000 значений.
  - `product_id` — ?. Фильтр по параметру `product_id`. Можно передавать до 1000 значений.
  - `visibility` — string (ALL, VISIBLE, INVISIBLE, EMPTY_STOCK, NOT_MODERATED, MODERATED, DISABLED, STATE_FAILED, READY_TO_SUPPLY, VALIDATION_STATE_PENDING, VALIDATION_STATE_FAIL, VALIDATION_STATE_SUCCESS…). Фильтр по видимости товара: - `ALL` — все товары, кроме архивных; - `VISIBLE` — товары, которые видны покупателям; - `INVISIBLE` — товары, которые не видны покупателям; - `EMPTY_STOCK` — товары, у которых не указано наличие; - `NOT_MODERATED` — товары, которые не прошли модерацию; - `MODERATED` — товары, которые прошли модерацию; - `DISABLED` — товары, которые видны покупателям, но недоступны к покупке; - `STATE_FAILED` — товары, создание которых завершилось ошибкой; - `READY_TO_SUPPLY` — товары, готовые к поставке; - `VALIDATION_STATE_PENDING` — товары, которые проходят проверку валидатором на премодерации; - `VALIDATION_STATE_FAIL` — товары, которые не прошли проверку валидатором на премодерации; - `VALIDATION_STATE_SUCCESS` — товары, которые прошли проверку валидатором на премодерации; - `TO_SUPPLY` — товары, готовые к продаже; - `IN_SALE` — товары в продаже; - `REMOVED_FROM_SALE` — товары, скрытые от покупателей; - `OVERPRICED` — товары с завышенной ценой; - `CRITICALLY_OVERPRICED` — товары со слишком завышенной ценой; - `EMPTY_BARCODE` — товары без штрихкода; - `BARCODE_EXISTS` — товары со штрихкодом; - `QUARANTINE` — товары на карантине после изменения цены более чем на 50%; - `ARCHIVED` — товары в архиве; - `OVERPRICED_WITH_STOCK` — товары в продаже со стоимостью выше, чем у конкурентов; - `PARTIAL_APPROVED` — товары в продаже с пустым или неполным описанием; - `AUTO_ARCHIVED` — товары, которые система перенесла в архив автоматически; - `MANUAL_ARCHIVED` — товары, которые продавец перенёс в архив вручную; - `SEASONAL_AUTO_ARCHIVED` — сезонные товары, которые система перенесла в архив автоматически; - `VISIBLE_WITH_FBO_STOCK` — товары с остатками на FBO, которые видят покупатели. По умолчанию: `ALL`.
- `limit` — integer<int32> **обязательный**. Количество значений на странице.

## Ответы

**200** — Информация о цене товара

- `cursor` — string. Указатель для выборки следующих данных.
- `items` — ?. Список товаров.
  - `acquiring` — number<double>. Максимальная комиссия за эквайринг. [Подробнее об эквайринге в Базе знаний продавца](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi#экваиринг)
  - `commissions` — object. Информация о комиссиях.
    - `fbo_deliv_to_customer_amount` — number<double>. Последняя миля (FBO).
    - `fbo_direct_flow_trans_max_amount` — number<double>. Магистраль до (FBO).
    - `fbo_direct_flow_trans_min_amount` — number<double>. Магистраль от (FBO).
    - `fbo_return_flow_amount` — number<double>. Комиссия за возврат и отмену (FBO).
    - `fbs_deliv_to_customer_amount` — number<double>. Последняя миля (FBS).
    - `fbs_direct_flow_trans_max_amount` — number<double>. Магистраль до (FBS).
    - `fbs_direct_flow_trans_min_amount` — number<double>. Магистраль от (FBS).
    - `fbs_first_mile_max_amount` — number<double>. Максимальная комиссия за обработку отправления (FBS). [Подробнее о тарифах в Базе знаний продавца](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi#выезд-транспортного-средства-по-адресу-продавца-для-забора-отправлении-(pick-up))
    - `fbs_first_mile_min_amount` — number<double>. Минимальная комиссия за обработку отправления (FBS). [Подробнее о тарифах в Базе знаний продавца](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi#выезд-транспортного-средства-по-адресу-продавца-для-забора-отправлении-(pick-up))
    - `fbs_return_flow_amount` — number<double>. Комиссия за возврат и отмену, обработка отправления (FBS).
    - `sales_percent_fbo` — number<double>. Процент комиссии за продажу (FBO).
    - `sales_percent_fbp` — number<double>. Процент комиссии за продажу (FBP).
    - `sales_percent_fbs` — number<double>. Процент комиссии за продажу (FBS).
    - `sales_percent_rfbs` — number<double>. Процент комиссии за продажу (rFBS).
  - `marketing_actions` — object. Маркетинговые акции.
    - `actions` — array[object]. Маркетинговые акции. Параметры `date_from`, `date_to`, `title` и `value` указываются для каждой акции.
      - `date_from` — string<date-time>. Дата и время начала акции.
      - `date_to` — string<date-time>. Дата и время окончания акции.
      - `title` — string. Название акции.
      - `value` — integer<int32>. Скидка по акции.
    - `current_period_from` — string<date-time>. Дата и время начала текущего периода по всем действующим акциям.
    - `current_period_to` — string<date-time>. Дата и время окончания текущего периода по всем действующим акциям.
    - `ozon_actions_exist` — boolean. `true`, если к товару можно применить акцию за счёт Ozon.
  - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
  - `price` — object. Цена товара.
    - `auto_action_enabled` — boolean. `true`, если автоприменение акций у товара включено.
    - `auto_add_to_ozon_actions_list_enabled` — boolean. `true`, если автодобавление товара в акции включено.
    - `currency_code` — string. Валюта ваших цен. Совпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
    - `marketing_seller_price` — number<double>. Предельная цена товара с учётом акций продавца, не учитывает дополнительную скидку от Ozon. Выше этого значения цену для покупателя не поднимем.
    - `min_price` — number<double>. Нижний порог предельной цены товара. Действует при автоприменении акций, автодобавлении товара в акции и в стратегиях ценообразования. Покупатели не видят это значение.
    - `net_price` — number<double>. Себестоимость товара.
    - `old_price` — number<double>. Цена, которую покупатели видят зачёркнутой. Должна быть больше `price`.
    - `price` — number<double>. Предельная цена товара без акций. Выше этого значения цену для покупателя не поднимем.
    - `retail_price` — number<double>. Цена поставщика по договору. Поле вернётся пустым, если нет договора на поставку.
    - `vat` — number<double>. Ставка НДС для товара.
  - `price_indexes` — object. Индексы цены товара. [Подробнее об индексе цен в Базе знаний продавца](https://seller-edu.ozon.ru/seller-rating/metrics/price-index)
    - `color_index` — string (WITHOUT_INDEX, GREEN, YELLOW, RED, SUPER). Итоговый индекс цены товара: - `WITHOUT_INDEX` — нет индекса, - `SUPER` — супервыгодный, - `GREEN` — выгодный, - `YELLOW` — умеренный, - `RED` — невыгодный. По умолчанию: `WITHOUT_INDEX`.
    - `external_index_data` — object. Цена товара у конкурентов на других площадках.
      - `min_price` — number<double>. Минимальная цена товара у конкурентов на другой площадке.
      - `min_price_currency` — string. Валюта цены.
      - `price_index_value` — number<double>. Значение индекса цены.
    - `ozon_index_data` — object. Цена товара у конкурентов на Ozon.
      - `min_price` — number<double>. Минимальная цена товара у конкурентов на Ozon.
      - `min_price_currency` — string. Валюта цены.
      - `price_index_value` — number<double>. Значение индекса цены.
    - `self_marketplaces_index_data` — object. Цена вашего товара на других площадках.
      - `min_price` — number<double>. Минимальная цена вашего товара на других площадках.
      - `min_price_currency` — string. Валюта цены.
      - `price_index_value` — number<double>. Значение индекса цены.
  - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
  - `volume_weight` — number<double>. Объёмный вес товара.
- `total` — integer<int32>. Количество товаров в списке.
- `total_items` — integer<int64>. Количество товаров в списке.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
