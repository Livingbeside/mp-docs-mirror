---
title: Список отправлений
api: ozon-seller
method: POST
path: /v2/posting/fbo/list
operation_id: PostingAPI_GetFboPostingList
tags:
  - FBO
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: ffcc4bc160a619b9
---

# Список отправлений

`POST /v2/posting/fbo/list`

> ⚠️ Метод помечен как **deprecated**.

С 31 августа 2026 года метод будет отключён. Переключитесь на [/v3/posting/fbo/list](#operation/PostingFboList).

Возвращает список отправлений за указанный период времени.
Если период больше года, вернётся ошибка `PERIOD_IS_TOO_LONG`.

Дополнительно можно отфильтровать отправления по их статусу.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `dir` — string. Направление сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию.
- `filter` — object **обязательный**. Фильтр для поиска отправлений.
  - `since` — string<date-time> **обязательный**. Начало периода.
  - `status` — string. Статус отправления. - `awaiting_packaging` — ожидает упаковки, - `awaiting_deliver` — ожидает отгрузки, - `delivering` — доставляется, - `delivered` — доставлено, - `cancelled` — отменено.
  - `to` — string<date-time> **обязательный**. Конец периода.
- `limit` — integer<int64> **обязательный**. Количество значений в ответе: - максимум — 1000, - минимум — 1.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента. Максимальное значение — 20000.
- `translit` — boolean. Если включена транслитерация адреса из кириллицы в латиницу — `true`.
- `with` — object. Дополнительные поля, которые нужно добавить в ответ.
  - `analytics_data` — boolean. Передайте `true`, чтобы добавить в ответ данные аналитики.
  - `financial_data` — boolean. Передайте `true`, чтобы добавить в ответ финансовые данные.
  - `legal_info` — boolean. Передайте `true`, чтобы добавить в ответ юридическую информацию.

## Ответы

**200** — Список отправлений

- `result` — array[object]. Массив отправлений.
  - `additional_data` — array[object]
    - `key` — string
    - `value` — string
  - `analytics_data` — object. Данные аналитики.
    - `city` — string. Город доставки. Только для продавцов из СНГ.
    - `client_delivery_date_begin` — string<date-time>. Дата и время начала доставки. Только для отправлений, оформленных через [Ozon Доставку](#tag/OzonLogistics).
    - `client_delivery_date_end` — string<date-time>. Ожидаемая дата, до которой заказ будет доставлен. Только для отправлений, оформленных через [Ozon Доставку](#tag/OzonLogistics).
    - `delivery_type` — string. Способ доставки.
    - `is_legal` — boolean. Получатель юридическое лицо: - `true` — юридическое лицо, - `false` — физическое лицо.
    - `is_premium` — boolean. Наличие подписки Premium.
    - `payment_type_group_name` — string. Способ оплаты: - `картой онлайн`, - `карта Ozon Банка`, - `автосписание с карты Ozon Банка при выдаче`, - `сохранённой картой при получении`, - `Система Быстрых Платежей`, - `Ozon Рассрочка`, - `оплата на расчётный счёт`, - `SberPay`, - `предоплата на стороне внешнего продавца`.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
    - `warehouse_name` — string. Название склада отправки заказа.
  - `cancel_reason_id` — integer<int64>. Идентификатор причины отмены отправления.
  - `created_at` — string<date-time>. Дата и время создания отправления.
  - `financial_data` — object. Финансовые данные.
    - `cluster_from` — string. Код региона, откуда отправляется заказ.
    - `cluster_to` — string. Код региона, куда доставляется заказ.
    - `products` — array[object]. Список товаров в заказе.
      - `actions` — array[string]. Список акций.
      - `commission_amount` — number<double>. Размер комиссии за товар.
      - `commission_percent` — integer<int64>. Процент комиссии.
      - `commissions_currency_code` — string. Код валюты, в которой рассчитывались комиссии.
      - `currency_code` — string. Валюта ваших цен. Cовпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
      - `old_price` — number<double>. Цена до учёта скидок. На карточке товара отображается зачёркнутой.
      - `payout` — number<double>. Выплата продавцу.
      - `price` — number<double>. Цена товара с учётом акций, кроме акций за счёт Ozon.
      - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
      - `quantity` — integer<int64>. Количество товара в отправлении.
      - `total_discount_percent` — number<double>. Процент скидки.
      - `total_discount_value` — number<double>. Сумма скидки.
  - `in_process_at` — string<date-time>. Дата и время начала обработки отправления.
  - `legal_info` — object. Юридическая информация о покупателе.
    - `company_name` — string. Название компании.
    - `inn` — string. ИНН.
    - `kpp` — string. КПП.
  - `order_id` — integer<int64>. Идентификатор заказа, к которому относится отправление.
  - `order_number` — string. Номер заказа, к которому относится отправление.
  - `posting_number` — string. Номер отправления.
  - `products` — array[object]. Список товаров в отправлении.
    - `currency_code` — string. Валюта ваших цен. Cовпадает с валютой, которая установлена в настройках личного кабинета. Возможные значения: - `RUB` — российский рубль, - `BYN` — белорусский рубль, - `KZT` — тенге, - `EUR` — евро, - `USD` — доллар США, - `CNY` — юань.
    - `digital_codes` — ?. Коды активации для услуг и цифровых товаров.
    - `is_marketplace_buyout` — boolean. `true`, если Ozon выкупил товар. [Подробнее о выкупе товаров в Базе знаний продавца](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/prodaji-tovarov-v-eaes-i-drugie-strany#какие-товары-выкупает-ozon)
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — string. Цена товара.
    - `quantity` — integer<int64>. Количество товара в отправлении.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string. Статус отправления: - `awaiting_packaging` — ожидает упаковки, - `awaiting_deliver` — ожидает отгрузки, - `delivering` — доставляется, - `delivered` — доставлено, - `cancelled` — отменено.
  - `substatus` — string. Подстатус отправления: - `posting_split_pending`, `posting_created` — создано; - `posting_packing` — на упаковке; - `posting_transferring_to_delivery` — передаётся в доставку; - `posting_on_way_to_city` — на пути в город доставки; - `posting_returned_to_warehouse` — возвращено на склад; - `posting_transferred_to_courier_service` — передаётся в службу доставки; - `posting_in_courier_service` — курьер в пути; - `posting_on_way_to_pickup_point` — в пути в пункт выдачи; - `posting_in_pickup_point` — в пункте выдачи; - `posting_delivered` — доставлено курьером; - `posting_received` — получено в пункте выдачи; - `posting_canceled` — отменено.

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
