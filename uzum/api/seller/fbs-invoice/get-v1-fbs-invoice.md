---
title: Получить все накладные для FBS заказа
api: uzum-seller
method: GET
path: /v1/fbs/invoice
operation_id: getFbsInvoices_1
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 1b22305e5118c667
---

# Получить все накладные для FBS заказа

`GET /v1/fbs/invoice`

Получить все накладные для FBS заказа

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `statuses` | query | array[string (CREATED, ACCEPTANCE_IN_PROGRESS, CANCELLED, ACCEPTED)] | да | Статус заказа |
| `size` | query | integer<int32> | нет | Кол-во записей на странице |
| `page` | query | integer<int32> | нет | Номер страницы |
| `Accept-Language` | header | string (ru, uz) | нет | Язык локализации. Поддерживаемые языки: ru, uz. По умолчанию: uz |

## Ответы

**403** — fbs-2-seller-access-denied - У продавца нет доступа

- `payload` — object. Response payload
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**200** — Success

- `payload` — array[object]. Response payload
  - `id` — integer<int64> **обязательный**. Уникальный идентификатор накладной
  - `number` — integer<int64> **обязательный**. Номер накладной, расчитывается по формуле: 120000000000 + идентификатор
  - `status` — object **обязательный**. Статус
    - `text` — string
    - `color` — string
    - `value` — string (CREATED, ACCEPTANCE_IN_PROGRESS, CANCELLED, ACCEPTED)
  - `fullPrice` — integer<int64> **обязательный**. Сумма всех заказов
  - `acceptedPrice` — integer<int64> **обязательный**. Сумма всех принятых заказов
  - `numberOrders` — integer<int64> **обязательный**. Количество заказов
  - `numberAcceptedOrders` — integer<int64> **обязательный**. Количество принятых заказов
  - `stock` — object **обязательный**
    - `id` — integer<int64>. Уникальный идентификатор склада
    - `externalId` — string. Внешний идентификатор склада
    - `title` — string. Название склада
    - `address` — string. Адрес склада
    - `timeFrom` — string. Время начала работы склада
    - `timeTo` — string. Время окончания работы склада
    - `poolSource` — string. Источник складских запасов
    - `dimensionalGroups` — array[object]. Список размерных групп, поддерживаемых складом
      - `group` — string (SMALL, MEDIUM, LARGE, UNKNOWN). Группа размеров: малый, средний, большой или неизвестный
      - `title` — string. Название размерной группы
  - `dateCreated` — string<date-time> **обязательный**. Дата создания
  - `dateUpdated` — string<date-time> **обязательный**. Дата обновления
  - `acceptanceStartedDate` — string<date-time> **обязательный**. Дата начала обработки на складе
  - `acceptedDate` — string<date-time> **обязательный**. Дата принятия на складе
  - `timeSlot` — object **обязательный**. Модель временного интервала
    - `timeFrom` — string<date-time>. Время начала временного интервала
    - `timeTo` — string<date-time>. Время окончания временного интервала
  - `dropOffPoint` — object **обязательный**. Пункт приема
    - `uuid` — string<uuid>. Идентификатор пункта приема
    - `address` — string. Адрес пункта приема
    - `type` — string (UNKNOWN, STOCK, ISSUE_POINT, UZ_POST, UCELL, NOT_UZUM, PHOTO_STUDIO, CROSS_DOCK, DROP_OFF_POINT, SORT_CENTER). Тип пункта доставки
  - `ettn` — object. ЭТТН
    - `ettnId` — string **обязательный**. ЭТТН
    - `isEditable` — boolean **обязательный**. Возможность редактирования ЭТТН
    - `status` — string (CREATED, CORRECT, INCORRECT, ETTN_ID_VALID, ETTN_ID_INVALID, DELETED) **обязательный**. Статус ЭТТН
    - `slaEttnUpdate` — string<date-time>. Время, до которого необходимо обновить ЭТТН
    - `warningFlag` — boolean **обязательный**. Флаг "Осталось меньше 24 часов до начала таймслота"
    - `lastUpdatedAt` — string<date-time>. Время последнего обновления ЭТТН селлером
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string

**404** — fbs-invoice-01 - Накладная не найдена

- `payload` — object. Response payload
- `errors` — array[object]
  - `code` — string **обязательный**. Код ошибки, который может помочь в определении причины.
  - `message` — string **обязательный**. Сообщение об ошибке, предназначенное для отображения пользователю.
  - `detailMessage` — string. Более подробное сообщение об ошибке. Возможно, устарело и больше не используется.
  - `payload` — object. Дополнительные данные, связанные с ошибкой.
- `timestamp` — string<date-time>
- `trace` — string
- `error` — string
