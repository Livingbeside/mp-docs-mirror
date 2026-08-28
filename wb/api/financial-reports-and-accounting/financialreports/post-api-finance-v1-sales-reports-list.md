---
title: Список отчётов реализации
api: wb-financial-reports-and-accounting
method: POST
path: /api/finance/v1/sales-reports/list
operation_id: postV1SalesReportsList
tags:
  - financialReports
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
deprecated: false
content_sha: 1277595283ede33d
---

# Список отчётов реализации

`POST /api/finance/v1/sales-reports/list`

Описание метода

 Метод доступен по
 Персональному токену, 
 Сервисному токену

Метод возвращает список отчётов релизации по формату [таблицы отчётов](https://seller.wildberries.ru/suppliers-mutual-settlements).

Данные доступны с 1 января 2025 года.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `dateFrom` — string **обязательный**. Начальная дата отчёта. Можно передать дату или дату со временем. Время можно указывать с точностью до секунд или миллисекунд. Дата передаётся в формате [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339), время — в часовом поясе Москва `UTC+3`. Примеры: - `2025-06-20` - `2025-06-20T23:59:59` - `2025-06-20T00:00:00.12345` - `2025-06-20T00:00:00`
- `dateTo` — string **обязательный**. Конечная дата отчёта. Дата в формате [RFC3339](https://datatracker.ietf.org/doc/html/rfc3339). Можно передать дату или дату со временем. Время можно указывать с точностью до секунд или миллисекунд. Время передаётся в часовом поясе Москва `UTC+3`. Примеры: - `2025-06-20` - `2025-06-20T23:59:59` - `2025-06-20T00:00:00.12345` - `2025-06-20T00:00:00`
- `limit` — integer. Количество отчётов в ответе По умолчанию: `1000`.
- `offset` — integer. Сколько элементов пропустить. Например, для значения `10` ответ начнётся с 11 элемента По умолчанию: `0`.
- `period` — string (daily, weekly). Периодичность отчётов: - `weekly` — еженедельные - `daily` — ежедневные По умолчанию: `weekly`.

## Ответы

**200** — Успешно

- `additionalPaymentSum` — string **обязательный**. Корректировка Вознаграждения Вайлдберриз (ВВ)
- `avgSalePercent` — number **обязательный**. Согласованная скидка, %
- `bankPaymentSum` — string **обязательный**. Итого к оплате
- `cashbackAmountSum` — string **обязательный**. Сумма, удержанная за начисленные баллы программы лояльности
- `cashbackCommissionChangeSum` — string **обязательный**. Стоимость участия в программе лояльности
- `cashbackDiscountSum` — string **обязательный**. Компенсация скидки по программе лояльности
- `createDate` — string<date> **обязательный**. Дата формирования отчёта
- `currency` — string **обязательный**. Валюта отчёта
- `dateFrom` — string<date> **обязательный**. Дата начала отчётного периода
- `dateTo` — string<date> **обязательный**. Дата конца отчётного периода
- `deductionSum` — string **обязательный**. Прочие удержания и выплаты
- `deliveryServiceSum` — string **обязательный**. Стоимость логистики
- `forPaySum` — string **обязательный**. К перечислению за товар
- `paidAcceptanceSum` — string **обязательный**. Стоимость операций при приёмке
- `paidStorageSum` — string **обязательный**. Стоимость хранения
- `paymentSchedule` — string **обязательный**. Разовое изменение срока перечисления денежных средств
- `penaltySum` — string **обязательный**. Общая сумма штрафов
- `reportId` — integer<int64> **обязательный**. ID отчёта
- `reportType` — integer (1, 2, 3) **обязательный**. Тип отчёта: - `1` — основной - `2` — по выкупам - `3` — по выкупам для Грузии
- `retailAmountSum` — string **обязательный**. Продажа
- `sellerFinanceName` — string **обязательный**. Наименование продавца

**204** — Нет данных

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
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

**403** — Доступ запрещён

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
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
