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
content_sha: b929d0198a2382a4
---

# Получить отчёт{{ /api/v1/paid_storage/tasks/{task_id}/download }}

`GET /api/v1/paid_storage/tasks/{task_id}/download`

Описание метода

Метод возвращает отчёт о [платном хранении](https://seller.wildberries.ru/analytics-reports/paid-storage/storage) по ID [задания на генерацию](./reports#tag/paidStorage/operation/getV1PaidStorage).

Лимит запросов на один профиль продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Сервисный | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый с секретом | 1 мин | 1 запрос | 1 мин | 1 запрос |
| Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `task_id` | path | string | да | ID задания на генерацию |

## Ответы

**200** — Успешно

- `date` — string **обязательный**. Дата расчёта или перерасчёта
- `logWarehouseCoef` — number **обязательный**. Коэффициент логистики и хранения. [На данный момент](/release-notes?id=570) может быть только `0`
- `officeId` — integer **обязательный**. ID склада. [На данный момент](/release-notes?id=570) может быть только `0`
- `warehouse` — string **обязательный**. Название склада. [На данный момент](/release-notes?id=570) может быть только `Склад WB РФ`
- `warehouseCoef` — number **обязательный**. Коэффициент хранения
- `giId` — integer **обязательный**. ID поставки
- `chrtId` — integer<uint64> **обязательный**. ID размера для этого артикула WB
- `size` — string **обязательный**. Размер (`techSize` в карточке товара)
- `barcode` — string **обязательный**. Баркод
- `subject` — string **обязательный**. Предмет
- `brand` — string **обязательный**. Бренд
- `vendorCode` — string **обязательный**. Артикул продавца
- `nmId` — integer **обязательный**. Артикул WB
- `volume` — number **обязательный**. Объём товара
- `calcType` — string **обязательный**. Способ расчёта
- `warehousePrice` — number **обязательный**. Сумма хранения
- `barcodesCount` — integer **обязательный**. Количество единиц товара (штук), подлежащих тарифицированию за расчётные сутки
- `palletPlaceCode` — integer **обязательный**. Код паллетоместа. [На данный момент](/release-notes?id=570) может быть только `0`
- `palletCount` — number **обязательный**. Количество паллет
- `originalDate` — string **обязательный**. Если был перерасчёт, это дата первоначального расчёта. Если перерасчёта не было, совпадает с `date`
- `loyaltyDiscount` — number **обязательный**. Скидка программы лояльности, ₽
- `tariffFixDate` — string **обязательный**. Дата фиксации тарифа
- `tariffLowerDate` — string **обязательный**. Дата понижения тарифа

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

**403** — Доступ запрещён

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

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
