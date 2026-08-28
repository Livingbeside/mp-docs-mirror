---
title: Установить оптовые скидки для B2B-продаж
api: wb-work-with-products
method: POST
path: /api/discounts-prices/v1/upload/task/b2b/wholesale
operation_id: postV1UploadTaskB2bWholesale
tags:
  - Цены и скидки
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: e6f16743d287ad85
---

# Установить оптовые скидки для B2B-продаж

`POST /api/discounts-prices/v1/upload/task/b2b/wholesale`

Описание метода

 Метод доступен по
 Персональному токену, 
 Сервисному токену

Метод устанавливает [оптовые скидки для бизнеса](https://seller.wildberries.ru/instructions/ru/ru/material/how-to-enable-wholesale-discounts-for-business)

 Получить информацию о процессе установки цен и скидок можно с помощью методов состояния и детализации обработанной загрузки.

Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов |
| Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `data` — array[object] **обязательный**. Товары и оптовые скидки для B2B
  - `nmId` — integer **обязательный**. Артикул WB
  - `wholesaleDiscountThreshold` — array[object] **обязательный**. Оптовые скидки разных уровней для B2B
    - `level` — integer **обязательный**. Уровень скидки
    - `minQuantity` — integer **обязательный**. Минимальное количество единиц товара для скидки
    - `wholesaleDiscount` — integer **обязательный**. Скидка, %. Чтобы удалить скидку, укажите `0`. Такой запрос одновременно удалит скидки на этом уровне и на всех более высоких уровнях `level` — вне зависимости от указания их в запросе

## Ответы

**200** — Успешно

- `alreadyExists` — boolean **обязательный**. Дублирование загрузки: `true` — такая загрузка уже есть
- `id` — integer **обязательный**. ID загрузки
- `results` — array[object] **обязательный**. Результаты обработки запроса
  - `error` — object. Ошибка. При `"success":false`
    - `detail` — string **обязательный**. Детали ошибки
    - `status` — integer **обязательный**. HTTP статус-код
    - `title` — string **обязательный**. Заголовок ошибки
  - `nmId` — integer **обязательный**. Артикул WB
  - `success` — boolean **обязательный**. Успешна ли установка скидки на товар: - `false` — неуспешна - `true` — успешна

**208** — Такая загрузка уже есть

- `detail` — string **обязательный**. Детали ответа
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ответа

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

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

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
