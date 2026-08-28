---
title: Получить список отправлений
api: ozon-seller
method: POST
path: /v1/posting/digital/list
operation_id: ListPostingCodes
tags:
  - Digital
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: true
content_sha: bc2ff88cee3d4a95
---

# Получить список отправлений

`POST /v1/posting/digital/list`

> ⚠️ Метод помечен как **deprecated**.

С 31 августа 2026 года метод будет отключён. Переключитесь на /v2/posting/digital/list.

Возвращает список отправлений, по которым нужно загрузить коды цифровых товаров. Метод доступен только продавцам, работающим с цифровыми товарами. 

Чтобы получить список отправлений в любом статусе, воспользуйтесь методом [/v2/posting/fbo/list](#operation/PostingAPI_GetFboPostingList).

## Запрос

**Тело запроса** (`application/json`):

- `dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию, - `DESC` — по убыванию.
- `filter` — object. Фильтр для поиска отправлений.
  - `posting_number` — array[string]. Номер отправления.
  - `since` — string<date-time>. Начало периода в формате `YYYY-MM-DD`.
  - `to` — string<date-time>. Конец периода в формате `YYYY-MM-DD`.
- `limit` — integer<int64>. Количество значений в ответе: - максимум — 1000, - минимум — 1.
- `offset` — integer<int64>. Количество элементов, которое будет пропущено в ответе. Например, если `offset = 10`, то ответ начнётся с 11-го найденного элемента. Максимальное значение — 20000.
- `with` — object. Дополнительные поля, которые нужно добавить в ответ.
  - `analytics_data` — boolean. Передайте `true`, чтобы добавить в ответ данные аналитики.
  - `financial_data` — boolean. Передайте `true`, чтобы добавить в ответ финансовые данные.
  - `legal_info` — boolean. Передайте `true`, чтобы добавить в ответ юридическую информацию.

## Ответы

**200** — Список отправлений

- `result` — array[object]. Список отправлений.
  - `additional_data` — array[object]. Дополнительные параметры.
    - `key` — string. Ключ дополнительного параметра.
    - `value` — string. Значение дополнительного параметра.
  - `analytics_data` — object. Данные аналитики.
    - `city` — string. Город доставки. Только для отправлений rFBS и продавцов из СНГ.
    - `delivery_type` — string. Способ доставки.
    - `is_legal` — boolean. Признак, что получатель юридическое лицо: - `true` — юридическое лицо, - `false` — физическое лицо.
    - `is_premium` — boolean. Наличие подписки Premium.
    - `payment_type_group_name` — string. Способ оплаты: - `картой онлайн`, - `карта Ozon Банка`, - `автосписание с карты Ozon Банка при выдаче`, - `сохранённой картой при получении`, - `Система Быстрых Платежей`, - `Ozon Рассрочка`, - `оплата на расчётный счёт`, - `SberPay`.
    - `region` — string. Регион доставки. Только для отправлений rFBS.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
    - `warehouse_name` — string. Название склада.
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
      - `customer_currency_code` — string. Код валюты покупателя.
      - `customer_price` — number<double>. Цена товара для покупателя с учётом скидок продавца и Ozon.
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
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — string. Цена товара.
    - `required_qty_for_digital_code` — integer<int32>. Количество кодов цифровых товаров, которое нужно передать по товару в отправлении. Передайте коды цифровых товаров с помощью метода [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes).
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string. Статус отправления: `awaiting_packaging` — ожидает упаковки.
  - `waiting_deadline_for_digital_code` — string<date-time>. Время, до которого нужно передать коды цифровых товаров. Передайте коды цифровых товаров с помощью метода [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes).

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
