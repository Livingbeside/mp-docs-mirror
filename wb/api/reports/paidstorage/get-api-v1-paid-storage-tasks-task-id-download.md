---
title: Получить отчёт{{ /api/v1/paid_storage/tasks/{task_id}/download }}
api: wb-reports
method: GET
path: /api/v1/paid_storage/tasks/{task_id}/download
operation_id: getV1PaidStorageTasksTaskIdDownload
tags:
  - paidStorage
spec_version: reports
source: "https://dev.wildberries.ru/docs/openapi/reports"
deprecated: false
content_sha: 9feccad048b95354
---

# Получить отчёт{{ /api/v1/paid_storage/tasks/{task_id}/download }}

`GET /api/v1/paid_storage/tasks/{task_id}/download`

Описание метода Метод возвращает отчёт о [платном хранении](https://seller.wildberries.ru/analytics-reports/paid-storage/storage) по ID [задания на генерацию](./reports#tag/paidStorage/operation/getV1PaidStorage). Лимит запросов на один аккаунт продавца: | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос | | Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос | | Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос | | Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `task_id` | path | string | да | ID задания на генерацию |

## Ответы

**200** — Успешно

- `date` — string. Дата, за которую был расчёт или перерасчёт
- `logWarehouseCoef` — number. Коэффициент логистики и хранения. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `0`
- `officeId` — integer. ID склада. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `0`
- `warehouse` — string. Название склада. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `Склад WB РФ`
- `warehouseCoef` — number. Коэффициент хранения
- `giId` — integer. ID поставки
- `chrtId` — integer. ID размера для этого артикула WB
- `size` — string. Размер (`techSize` в карточке товара)
- `barcode` — string. Баркод
- `subject` — string. Предмет
- `brand` — string. Бренд
- `vendorCode` — string. Артикул продавца
- `nmId` — integer. Артикул WB
- `volume` — number. Объём товара
- `calcType` — string. Способ расчёта
- `warehousePrice` — number. Сумма хранения
- `barcodesCount` — integer. Количество единиц товара (штук), подлежащих тарифицированию за расчётные сутки
- `palletPlaceCode` — integer. Код паллетоместа. [На данный момент](https://dev.wildberries.ru/release-notes?id=570) может быть только `0`
- `palletCount` — number. Количество паллет
- `originalDate` — string. Если был перерасчёт, это дата первоначального расчёта. Если перерасчёта не было, совпадает с `date`
- `loyaltyDiscount` — number. Скидка программы лояльности, ₽
- `tariffFixDate` — string. Дата фиксации тарифа
- `tariffLowerDate` — string. Дата понижения тарифа

**204** — Нет данных

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

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

**404** — Не найдено

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
