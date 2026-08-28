---
title: Получить список заявок на скидку
api: ozon-seller
method: POST
path: /v2/actions/discounts-task/list
operation_id: GetDiscountTaskListV2
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: e48bff061186b00a
---

# Получить список заявок на скидку

`POST /v2/actions/discounts-task/list`

Возвращает список товаров, которые покупатели хотят купить со скидкой. Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/1856-Novye-metody-dlia-raboty-s-polucheniem-Spiska-zaiavok-na-skidku/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `last_id` — integer<int64>. Идентификатор последнего значения на странице. При первом запросе оставьте это поле пустым.
- `limit` — integer (5, 10, 15, 20, 30, 50). Максимальное количество заявок на странице. По умолчанию: `50`.
- `status` — string (ALL, NEW, APPROVED, DECLINED). Статус заявки на скидку: - `ALL` — все статусы, - `NEW` — новая, - `APPROVED` — одобренная, - `DECLINED` — отклонённая. По умолчанию: `ALL`.

## Ответы

**200** — Список заявок

- `tasks` — array[object]. Список заявок.
  - `approved_discount` — number<double>. Скидка в рублях, которую одобрил продавец. Передайте значение `0`, если продавец не одобрил заявку.
  - `approved_price` — number<double>. Одобренная цена.
  - `approved_quantity_max` — integer<uint64>. Максимальное одобренное количество товаров.
  - `auto_moderated_info` — object. Информация об автоматической модерации заявки.
    - `max_percent` — number<double>. Максимальная скидка для одобрения.
    - `max_price` — number<double>. Цена в заявке.
    - `min_percent` — number<double>. Минимальная скидка для одобрения.
    - `min_price` — number<double>. Минимальная цена для одобрения.
  - `created_at` — string<date-time>. Дата создания заявки.
  - `edited_till` — string<date-time>. Время для изменения решения.
  - `edited_till_duration` — integer<uint64>. Время для изменения решения в секундах.
  - `email` — string. Электронный адрес сотрудника продавца, который обработал заявку.
  - `end_at` — string<date-time>. Время окончания действия заявки.
  - `end_at_duration` — integer<uint64>. Время окончания действия заявки в секундах.
  - `first_name` — string. Имя сотрудника продавца, который обработал заявку.
  - `id` — integer<uint64>. Идентификатор заявки.
  - `is_auto_moderated` — boolean. `true`, если модерация была автоматической.
  - `last_name` — string. Фамилия сотрудника продавца, который обработал заявку.
  - `min_auto_price` — number<double>. Минимальное значение цены после автоприменения скидок и акций.
  - `moderated_at` — string<date-time>. Дата модерации: просмотра, одобрения или отклонения заявки.
  - `name` — string. Название товара.
  - `original_price` — number<double>. Цена товара до всех скидок.
  - `patronymic` — string. Отчество сотрудника продавца, который обработал заявку.
  - `reduction_factor` — number<double>. Разница между ценой пользователя и продавца в момент создания заявки.
  - `requested_discount` — number<double>. Скидка в процентах.
  - `requested_price` — number<double>. Цена по заявке.
  - `requested_quantity_max` — integer<uint64>. Запрошенное максимальное количество товаров.
  - `sku` — integer<uint64>. Идентификатор товара в системе Ozon — SKU.
  - `status` — string (ALL, NEW, APPROVED, DECLINED). Статус заявки на скидку: - `ALL` — все статусы, - `NEW` — новая, - `APPROVED` — одобренная, - `DECLINED` — отклонённая. По умолчанию: `ALL`.

**default** — Ошибка

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
