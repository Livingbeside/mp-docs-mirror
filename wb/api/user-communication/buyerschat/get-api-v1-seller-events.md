---
title: События чатов
api: wb-user-communication
method: GET
path: /api/v1/seller/events
operation_id: getV1SellerEvents
tags:
  - buyersChat
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: fb879a288ac018ac
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

- `errors` — array[string]. Ошибки, если есть
- `result` — object
  - `events` — array[object]
    - `addTime` — string. Время появления события на сервере в UTC
    - `addTimestamp` — integer. Время появления события на сервере. Формат Unix timestamp
    - `chatID` — string. ID чата
    - `clientName` — string. Имя покупателя
    - `eventID` — string. ID события
    - `eventType` — string (message). Тип события: - `message` — сообщение
    - `isNewChat` — boolean. Признак нового чата: - `false` — чат не новый - `true` — чат новый
    - `message` — object. Данные сообщения
      - `attachments` — object. Вложения
        - `files` — array[object]. Файлы
          - `contentType` — string. Тип файла
          - `date` — string. Дата загрузки файла
          - `downloadID` — string. ID файла. [Получить файл](./user-communication#tag/buyersChat/operation/getV1SellerDownloadId)
          - `name` — string. Название файла
          - `size` — integer. Размер файла в байтах
          - `url` — string. URL для получения файла
        - `goodCard` — object. Информация о заказе
          - `nmID` — integer. Артикул WB
          - `price` — integer. Фактическая цена с учетом всех скидок. Взимается с покупателя
          - `priceCurrency` — string. Валюта
          - `rid` — string. Уникальный ID заказа. Примечание: `rid` — это `srid` в ответах методов: - [Заявки покупателей на возврат](./user-communication#tag/buyersReturns/operation/getV1Claims) - [Лента заказов](./analytics#tag/orderFeed/operation/postV1OrderFeed) - [Заказы](./reports#tag/mainReports/operation/getV1SupplierOrders) - [Продажи](./reports#tag/mainReports/operation/getV1SupplierSales) - [Отчёт о возвратах и перемещении товаров](./reports#tag/returnsAndItemMovementReport) - [Детализации к отчётам реализации по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailedReportId) - [Детализации к отчётам реализации за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1SalesReportsDetailed) - [Детализации к отчётам об издержках на приём платежей по ID отчётов](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailedReportId) - [Детализации к отчётам об издержках на приём платежей за период](./financial-reports-and-accounting#tag/financialReports/operation/postV1AcquiringDetailed)
          - `size` — string. Размер товара, соответствует `wbSize` в [карточке товара](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post)
        - `images` — array[object]. Изображения
          - `date` — string. Дата загрузки изображения
          - `downloadID` — string. ID файла. [Получить файл](./user-communication#tag/buyersChat/operation/getV1SellerDownloadId)
          - `url` — string. URL для получения изображения
      - `text` — string. Текст сообщения
    - `replySign` — string. Подпись чата. Доступна только при `"isNewChat": true`. Требуется при [отправке сообщения](./user-communication#tag/buyersChat/operation/postV1SellerMessage)
    - `sender` — string (client, seller, wb). Отправитель: - `client` — покупатель - `seller` — продавец - `wb` — Wildberries
    - `source` — string. Источник отправки сообщения: - `seller-portal` — портал продавцов - `seller-public-api` — API Чата с покупателями - `rusite` — портал покупателей - `global` — портал `global.wildberries.ru` - `ios` — мобильная операционная система от **Apple** - `android` — операционная система **Android** от **Google**
  - `newestEventTime` — string<date-time>. Время новейшего события в ответе
  - `next` — integer<Unix timestamp>. Пагинатор. Значение поля необходимо указать в запросе для получения следующего пакета данных
  - `oldestEventTime` — string<date-time>. Время старейшего события в ответе
  - `totalEvents` — integer. Количество событий

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `error` — string. Текст ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `title` — string. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
