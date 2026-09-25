---
title: Получение списка расходов продавца.
api: uzum-seller
method: GET
path: /v1/finance/expenses
operation_id: getFinanceExpenses
tags:
  - Finance
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: a99d0f8fed565d1c
---

# Получение списка расходов продавца.

`GET /v1/finance/expenses`

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `page` | query | integer<int32> | нет | Номер страницы для постраничного вывода данных. |
| `size` | query | integer<int32> | нет | Количество элементов на странице. |
| `shopId` | query | integer<int64> | нет | Идентификатор магазина для выборки данных. |
| `shopIds` | query | array[integer<int64>] | нет | Список идентификаторов магазинов для выборки данных. |
| `dateFrom` | query | integer<int64> | нет | Начальная дата для фильтрации расходов. |
| `dateTo` | query | integer<int64> | нет | Конечная дата для фильтрации расходов. |
| `sources` | query | array[string] | нет | Источники, по которым фильтруются расходы. |

## Ответы

**200** — OK

- `payload` — object. Список информации о платежах продавца.
  - `payments` — array[object]. Массив объектов, содержащих данные о платежах продавца.
    - `id` — integer<int64>. Уникальный идентификатор платежа.
    - `dateCreated` — string<date-time>. Дата и время создания записи о платеже.
    - `dateUpdated` — string<date-time>. Дата и время последнего обновления записи о платеже.
    - `name` — string. Название платежа или его описание.
    - `source` — string. Источник, из которого был инициирован платеж.
    - `shopId` — integer<int64>. Идентификатор магазина, связанного с платежом.
    - `sellerId` — integer<int64>. Идентификатор продавца, связанного с платежом.
    - `paymentPrice` — integer<int64>. Сумма платежа.
    - `amount` — integer<int32>. Количество единиц, связанных с платежом.
    - `status` — string (CREATED, REFUNDED, CONFIRMED, CANCELED). Статус платежа: CREATED - создан, REFUNDED - возвращен, CONFIRMED - подтвержден, CANCELED - отменен.
    - `externalId` — string. Внешний идентификатор платежа.
    - `code` — string. Код, связанный с платежом.
    - `dateService` — string<date-time>. Дата и время оказания услуги, связанной с платежом.
    - `type` — string (OUTCOME, INCOME). Тип платежа: OUTCOME - исходящий платеж, INCOME - входящий платеж.
- `errors` — array[object]. Список ошибок, возникших во время обработки запроса.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Временная метка, указывающая время выполнения запроса.
- `trace` — string. Идентификатор трассировки для отладки.
- `error` — string. Код ошибки, если запрос завершился с ошибкой.

**400** — Bad Request

- `payload` — object. Данные ответа, содержит информацию об объекте, возвращаемом сервисом.
- `errors` — array[object]. Список ошибок, если запрос не был успешно выполнен.
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>. Время формирования ответа, формат даты и времени.
- `trace` — string. Трассировка для отладки ошибок.
- `error` — string. Сообщение об ошибке, если оно имеется.
