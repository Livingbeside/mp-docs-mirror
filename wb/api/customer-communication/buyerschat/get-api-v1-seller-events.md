---
title: События чатов
api: wb-customer-communication
method: GET
path: /api/v1/seller/events
operation_id: getV1SellerEvents
tags:
  - buyersChat
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: 9890fdd9d052e90d
---

# События чатов

`GET /api/v1/seller/events`

Описание метода

Метод возвращает список событий всех [чатов с покупателями](./user-communication#tag/buyersChat/operation/getV1SellerChats).

Чтобы получить все события:
 1. Сделайте первый запрос без параметра `next`.
 2. Повторяйте запрос со значением параметра `next` из ответа на предыдущий запрос, пока `totalEvents` не станет равным `0`. Это будет означать, что вы получили все события.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Сервисный | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый с секретом | 10 сек | 10 запросов | 1 сек | 10 запросов |
| Базовый | 1 ч | 1 запрос | 1 ч | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `next` | query | integer | нет | Пагинатор. С какого момента получить следующий пакет данных. Формат Unix timestamp **с миллисекундами** |

## Ответы

**200** — Успешно

- `result` — object
  - `next` — integer<Unix timestamp>. Пагинатор. Значение поля необходимо указать в запросе для получения следующего пакета данных
  - `newestEventTime` — string<date-time>. Время новейшего события в ответе
  - `oldestEventTime` — string<date-time>. Время старейшего события в ответе
  - `totalEvents` — integer. Количество событий
  - `events` — array[object]
    - `chatID` — string. ID чата
    - `eventID` — string. ID события
    - `eventType` — string (message). Тип события: - `message` — сообщение
    - `isNewChat` — boolean. Признак нового чата: - `false` — чат не новый - `true` — чат новый
    - `message` — object. Данные сообщения
      - `attachments` — object. Вложения
        - `goodCard` — object. Информация о заказе
          - `nmID` — integer. Артикул WB
          - `price` — integer. Фактическая цена с учетом всех скидок. Взимается с покупателя
          - `priceCurrency` — string. Валюта
          - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./user-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
          - `size` — string. Размер товара, соответствует `wbSize` в [карточке товара](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post)
        - `files` — array[object]. Файлы
          - `contentType` — string. Тип файла
          - `date` — string. Дата загрузки файла
          - `downloadID` — string. ID файла. [Получить файл](./user-communication#tag/buyersChat/operation/getV1SellerDownloadId)
          - `name` — string. Название файла
          - `url` — string. URL для получения файла
          - `size` — integer. Размер файла в байтах
        - `images` — array[object]. Изображения
          - `date` — string. Дата загрузки изображения
          - `downloadID` — string. ID файла. [Получить файл](./user-communication#tag/buyersChat/operation/getV1SellerDownloadId)
          - `url` — string. URL для получения изображения
      - `text` — string. Текст сообщения
    - `source` — string. Источник отправки сообщения: - `seller-portal` — портал продавцов - `seller-public-api` — API Чата с покупателями - `rusite` — портал покупателей - `global` — портал `global.wildberries.ru` - `ios` — мобильная операционная система от **Apple** - `android` — операционная система **Android** от **Google**
    - `addTimestamp` — integer. Время появления события на сервере. Формат Unix timestamp
    - `addTime` — string. Время появления события на сервере в UTC
    - `replySign` — string. Подпись чата. Доступна только при `"isNewChat": true`. Требуется при [отправке сообщения](./user-communication#tag/buyersChat/operation/postV1SellerMessage)
    - `sender` — string (client, seller, wb). Отправитель: - `client` — покупатель - `seller` — продавец - `wb` — Wildberries
    - `clientName` — string. Имя покупателя
- `errors` — array[string]. Ошибки, если есть

**400** — Неправильный запрос

- `status` — number. HTTP статус-код
- `title` — string. Заголовок ошибки
- `origin` — string. ID внутреннего сервиса WB
- `detail` — string. Детали ошибки
- `requestId` — string. Уникальный ID запроса
- `error` — string. Текст ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
