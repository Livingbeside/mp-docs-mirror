---
title: Получить накладную по идентифкатору
api: uzum-seller
method: GET
path: /v1/fbs/invoice/{invoiceId}
operation_id: getFbsInvoice_byId
tags:
  - FBS Invoice
spec_version: 1.0.0
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
deprecated: false
content_sha: 2fe6c1753bc416d0
---

# Получить накладную по идентифкатору

`GET /v1/fbs/invoice/{invoiceId}`

Return fbs invoice

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | path | integer<int64> | да | Идентификатор накладной |
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

- `payload` — object. Response payload
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
