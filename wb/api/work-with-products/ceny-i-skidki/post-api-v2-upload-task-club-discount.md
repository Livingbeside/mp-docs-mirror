---
title: Установить скидки WB Клуба
api: wb-work-with-products
method: POST
path: /api/v2/upload/task/club-discount
operation_id: post-api-v2-upload-task-club-discount
tags:
  - Цены и скидки
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 68adc3fb340c57a4
---

# Установить скидки WB Клуба

`POST /api/v2/upload/task/club-discount`

Описание метода

Устанавливает скидки для товаров в рамках подписки [WB Клуб](https://seller.wildberries.ru/help-center/article/A-337).

 Получить информацию о процессе установки цен и скидок можно с помощью методов [состояния](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1history~1tasks/get) и [детализации](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1history~1goods~1task/get) обработанной загрузки.

Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый с секретом | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Базовый | 1 ч | 4 запроса | 15 мин | 1 запрос |

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Запрос

**Тело запроса** (`application/json`):

- `data` — array[object] **обязательный**. Товары и скидки WB Клуба для них. Максимум 1 000 товаров.
  - `clubDiscount` — integer **обязательный**. Скидка WB Клуба, %
  - `nmID` — integer **обязательный**. Артикул WB

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `alreadyExists` — boolean. Флаг дублирования загрузки: `true` — такая загрузка уже есть
  - `id` — integer. ID загрузки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**208** — Такая загрузка уже есть

- `data` — object. Данные ответа
  - `alreadyExists` — boolean. Флаг дублирования загрузки: `true` — такая загрузка уже есть
  - `id` — integer. ID загрузки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

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

**403** — Доступ запрещён

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**409** — Ошибка при конвертации валюты

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**422** — Неожидаемый результат

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
