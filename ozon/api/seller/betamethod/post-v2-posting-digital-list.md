---
title: Получить список отправлений
api: ozon-seller
method: POST
path: /v2/posting/digital/list
operation_id: PostingDigitalList
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 4e47fc74924596a5
---

# Получить список отправлений

`POST /v2/posting/digital/list`

Возвращает список отправлений, по которым нужно загрузить коды цифровых товаров. Метод доступен только продавцам, которые работают с цифровыми товарами. 

Чтобы получить список отправлений в любом статусе, используйте метод [/v3/posting/fbo/list](#operation/PostingFboList).

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2050-Novyi-beta-metod-dlia-postingov-s-zagruzkoi-kodov-tsifrovykh-tovarov-v-Seller-API/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `cursor` — string. Указатель для выборки следующих данных.
- `filter` — object. Фильтр для поиска отправлений.
  - `order_numbers` — array[string]. Номера заказов, к которым относятся отправления.
  - `posting_numbers` — array[string]. Идентификаторы отправлений.
  - `since` — string<date-time>. Начало периода.
  - `to` — string<date-time>. Конец периода.
- `limit` — integer<int64>. Количество значений в ответе.
- `sort_dir` — string (ASC, DESC). Направление сортировки: - `ASC` — по возрастанию; - `DESC` — по убыванию.
- `with` — object. Дополнительные поля, которые нужно добавить в ответ.
  - `analytics_data` — boolean. `true`, чтобы добавить в ответ данные аналитики.
  - `financial_data` — boolean. `true`, чтобы добавить в ответ финансовые данные.
  - `legal_info` — boolean. `true`, чтобы добавить в ответ юридическую информацию.

## Ответы

**200** — Список отправлений

- `cursor` — string. Указатель для выборки следующих данных.
- `has_next` — boolean. `true`, если в ответе вернулись не все отправления.
- `postings` — array[object]. Список отправлений.
  - `additional_data` — array[object]. Дополнительные параметры.
    - `key` — string. Ключ дополнительного параметра.
    - `value` — string. Значение дополнительного параметра.
  - `analytics_data` — object. Данные аналитики.
    - `city` — string. Город доставки. Только для отправлений rFBS и продавцов из СНГ.
    - `delivery_type` — string. Способ доставки.
    - `is_legal` — boolean. `true`, если получатель юридическое лицо.
    - `is_premium` — boolean. `true`, если у получателя есть подписка Premium.
    - `payment_type_group_name` — string. Способ оплаты: - `картой онлайн`; - `карта Ozon Банка`; - `автосписание с карты Ozon Банка при выдаче`; - `сохранённой картой при получении`; - `Система Быстрых Платежей`; - `Ozon Рассрочка`; - `оплата на расчётный счёт`; - `SberPay`; - `предоплата на стороне внешнего продавца`.
    - `region` — string. Регион доставки. Только для отправлений rFBS.
    - `warehouse_id` — integer<int64>. Идентификатор склада.
    - `warehouse_name` — string. Название склада отправки заказа.
  - `cancel_reason_id` — integer<int64>. Идентификатор причины отмены отправления.
  - `cancellation` — object. Информация об отмене.
    - `cancellation_initiator` — string. Инициатор отмены: - `Продавец`, - `Клиент`, - `Покупатель`, - `Ozon`, - `Система`, - `Служба доставки`.
    - `cancellation_type` — string. Тип отмены: - `seller` — отменено продавцом; - `client` или `customer` — отменено покупателем; - `ozon` — отменено Ozon; - `system` — отменено системой; - `delivery` — отменено службой доставки.
  - `created_at` — string<date-time>. Дата и время создания отправления.
  - `external_order` — object. Информация о заказе с внешней платформы.
    - `is_external` — boolean. `true`, если заказ с внешней платформы.
    - `platform_name` — string. Название платформы, с которой сделали заказ.
  - `financial_data` — object. Финансовые данные.
    - `cluster_from` — string. Код региона, откуда отправляется заказ.
    - `cluster_to` — string. Код региона, куда доставляется заказ.
    - `products` — array[object]. Список товаров в заказе.
      - `actions` — array[string]. Список акций.
      - `commission` — object. Комиссия за товар.
        - `amount` — number<double>. Размер комиссии за товар.
        - `currency` — string. Код валюты, в которой рассчитывалась комиссия.
        - `percent` — integer<int64>. Процент комиссии.
      - `old_price` — number<double>. Цена до учёта скидок. На карточке товара отображается зачёркнутой.
      - `payout` — number<double>. Выплата продавцу.
      - `price` — number<double>. Цена товара с учётом акций, кроме акций за счёт Ozon.
      - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
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
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — object. Цена товара.
      - `amount` — string. Сумма.
      - `currency` — string. Валюта.
    - `quantity` — integer<int64>. Количество товара в отправлении.
    - `required_qty_for_digital_code` — integer<int32>. Количество кодов цифровых товаров, которые нужно передать по товару в отправлении. Передайте коды цифровых товаров с помощью метода [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes).
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string. Статус отправления: `awaiting_packaging` — ожидает упаковки.
  - `waiting_deadline_for_digital_code` — string<date-time>. Время, до которого нужно передать коды цифровых товаров. Передайте коды цифровых товаров с помощью метода [/v1/posting/digital/codes/upload](#operation/UploadPostingCodes).

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
