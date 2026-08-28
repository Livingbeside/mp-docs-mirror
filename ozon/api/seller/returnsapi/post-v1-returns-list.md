---
title: Информация о возвратах FBO и FBS
api: ozon-seller
method: POST
path: /v1/returns/list
operation_id: returnsList
tags:
  - ReturnsAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 6541bcca6b847cc0
---

# Информация о возвратах FBO и FBS

`POST /v1/returns/list`

Метод для получения информации о возвратах FBO и FBS.

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object. Фильтры. Используйте только один фильтр в запросе: `logistic_return_date`, `storage_tariffication_start_date` или `visual_status_change_moment`, иначе вернётся ошибка.
  - `barcode` — string. Фильтр по штрихкоду возвратной этикетки.
  - `compensation_status_id` — integer<int32>. Фильтр по статусу компенсации: - `1` — отправлена; - `2` — получена; - `3` — отменена; - `4` — проведена декомпенсация.
  - `logistic_return_date` — object. Фильтр по дате создания возврата.
    - `time_from` — string<date-time>. Начало периода.
    - `time_to` — string<date-time>. Окончание периода.
  - `offer_id` — string. Фильтр по артикулу товара.
  - `order_id` — integer<int64>. Фильтр по идентификатору заказа.
  - `posting_numbers` — array[string]. Фильтр по номеру отправления. Передавайте не больше 50 постингов.
  - `product_name` — string. Фильтр по названию товара.
  - `return_schema` — string. Фильтр по схеме доставки: `FBS` или `FBO`.
  - `storage_tariffication_start_date` — object. Фильтр по дате начала тарификации.
    - `time_from` — string<date-time>. Начало периода.
    - `time_to` — string<date-time>. Окончание периода.
  - `visual_status_change_moment` — object. Фильтр по дате изменения статуса возврата.
    - `time_from` — string<date-time>. Начало периода.
    - `time_to` — string<date-time>. Окончание периода.
  - `visual_status_name` — string. Фильтр по статусу возврата: - `DisputeOpened` — открыт спор с покупателем; - `OnSellerApproval` — на согласовании у продавца; - `ArrivedAtReturnPlace` — в пункте выдачи; - `OnSellerClarification` — на уточнении у продавца; - `OnSellerClarificationAfterPartialCompensation` — на уточнении у продавца после частичной компенсации; - `OfferedPartialCompensation` — предложена частичная компенсация; - `ReturnMoneyApproved` — одобрен возврат денег; - `PartialCompensationReturned` — вернули часть денег; - `CancelledDisputeNotOpen` — возврат отклонён, спор не открыт; - `Rejected` — заявка отклонена; - `CrmRejected` — заявка отклонена Ozon; - `Cancelled` — заявка отменена; - `Approved` — заявка одобрена продавцом; - `ApprovedByOzon` — заявка одобрена Ozon; - `ReceivedBySeller` — продавец получил возврат; - `MovingToSeller` — возврат на пути к продавцу; - `ReturningToSellerByCourier` — курьер везёт возврат продавцу; - `Utilizing` — на утилизации; - `Utilized` — утилизирован; - `MoneyReturned` — покупателю вернули всю сумму; - `PartialCompensationInProcess` — одобрен частичный возврат денег; - `DisputeYouOpened` — продавец открыл спор; - `CompensationRejected` — отказано в компенсации; - `DisputeOpening` — обращение в поддержку отправлено; - `CompensationOffered` — ожидает вашего решения по компенсации; - `WaitingCompensation` — ожидает компенсации; - `SendingError` — ошибка при отправке обращения в поддержку; - `CompensationRejectedBySla` — истёк срок решения; - `CompensationRejectedBySeller` — продавец отказался от компенсации; - `MovingToOzon` — едет на склад Ozon; - `ReturnedToOzon` — на складе Ozon; - `MoneyReturnedBySystem` — быстрый возврат; - `WaitingShipment` — ожидает отправки.
  - `warehouse_id` — integer<int64>. Фильтр по идентификатору склада. Можно получить с помощью метода [/v1/warehouse/list](#operation/WarehouseAPI_WarehouseList).
- `last_id` — integer<int64>. Идентификатор последнего подгруженного возврата.
- `limit` — integer<int32> **обязательный**. Количество подгружаемых возвратов. Максимальное значение — 500.

## Ответы

**200** — Информация по возвратам

- `has_next` — boolean. `true`, если у продавца есть другие возвраты.
- `returns` — array[object]. Информация о возвратах.
  - `additional_info` — object. Дополнительная информация.
    - `is_opened` — boolean. `true`, если возврат вскрыт.
    - `is_super_econom` — boolean. `true`, если возврат относится к товарам «Суперэконом».
  - `clearing_id` — integer<int64>. Штрихкод изначального отправления.
  - `company_id` — integer<int64>. Идентификатор продавца.
  - `compensation_status` — object. Информация о статусе компенсации.
    - `change_moment` — string<date-time>. Дата изменения статуса компенсации.
    - `status` — object. Статус компенсации.
      - `display_name` — string. Название статуса: - «Отправлено на компенсацию», - «Вы получили компенсацию», - «Компенсация отменена», - «Провели декомпенсацию».
      - `id` — integer<int32>. Идентификатор статуса.
      - `sys_name` — string. Системное название статуса: - `Sent` — отправлена; - `Received` — получена; - `Canceled` — отменена; - `DecompensationSent` — проведена декомпенсация.
  - `exemplars` — array[object]. Информация об экземплярах.
    - `id` — integer<int64>. Идентификатор экземпляра.
  - `id` — integer<int64>. Идентификатор возврата.
  - `logistic` — object. Информация о возврате.
    - `barcode` — string. Штрихкод этикетки возврата.
    - `cancelled_with_compensation_moment` — string<date-time>. Дата, когда продавцу компенсировали возврат.
    - `final_moment` — string<date-time>. Дата, когда возврат прибыл на фулфилмент или выдан продавцу.
    - `return_date` — string<date-time>. Дата, когда покупатель вернул товар.
    - `technical_return_moment` — string<date-time>. Дата, когда заказ поставили на технический возврат.
  - `order_id` — integer<int64>. Идентификатор заказа.
  - `order_number` — string. Номер заказа.
  - `place` — object. Склад, где находится возврат.
    - `address` — string. Адрес.
    - `id` — integer<int64>. Идентификатор склада.
    - `name` — string. Название.
  - `posting_number` — string. Номер отправления.
  - `product` — object. Информация о товаре.
    - `commission` — object. Информация о комиссии.
      - `currency_code` — string. Валюта.
      - `price` — number<double>. Размер комиссии.
    - `commission_percent` — number<double>. Процент комиссии.
    - `name` — string. Название товара.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул.
    - `price` — object. Стоимость товара.
      - `currency_code` — string. Валюта.
      - `price` — number<double>. Стоимость товара.
    - `price_without_commission` — object. Стоимость товара без комиссии.
      - `currency_code` — string. Валюта.
      - `price` — number<double>. Стоимость товара без комиссии.
    - `quantity` — integer<int32>. Количество товара.
    - `sku` — integer<int64>. Идентификатор товара в системе Ozon — SKU.
  - `return_clearing_id` — integer<int64>. Возвратный штрихкод изначального отправления.
  - `return_reason_name` — string. Причина возврата или отмены.
  - `schema` — string. Схема возврата: `FBS`; `FBO`.
  - `source_id` — integer<int64>. Предыдущий идентификатор возврата.
  - `storage` — object. Информация о хранении.
    - `arrived_moment` — string<date-time>. Дата, когда возврат был готов к выдаче.
    - `days` — integer<int64>. Сколько дней возврат ожидает выдачи продавцу.
    - `sum` — object. Стоимость хранения.
      - `currency_code` — string. Валюта.
      - `price` — number<double>. Стоимость хранения.
    - `tariffication_first_date` — string<date-time>. Первый день тарификации за хранение.
    - `tariffication_start_date` — string<date-time>. Дата старта тарификации за хранение.
    - `utilization_forecast_date` — string. Планируемая дата утилизации.
    - `utilization_sum` — object. Стоимость утилизации.
      - `currency_code` — string. Валюта.
      - `price` — number<double>. Стоимость утилизации.
  - `target_place` — object. Склад, куда едет возврат.
    - `address` — string. Адрес.
    - `id` — integer<int64>. Идентификатор склада.
    - `name` — string. Название.
  - `type` — string. Тип возврата: `Cancellation` - отмена (до вручения); `FullReturn` - полный отказ при вручении; `PartialReturn` - частичный отказ при вручении; `ClientReturn` - клиентский возврат (после вручения); `Unknown` - технический возврат.
  - `visual` — object. Информация о статусе возврата.
    - `change_moment` — string<date-time>. Дата изменения статуса возврата.
    - `status` — object. Статус возврата.
      - `display_name` — string. Название статуса возврата.
      - `id` — integer<int32>. Идентификатор статуса возврата.
      - `sys_name` — string. Системное название статуса возврата.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
