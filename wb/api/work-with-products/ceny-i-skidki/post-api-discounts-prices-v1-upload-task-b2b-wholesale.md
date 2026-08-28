---
title: Установить оптовые скидки для B2B-продаж{{ /api/discounts-prices/v1/upload/task/b2b/wholesale }}
api: wb-work-with-products
method: POST
path: /api/discounts-prices/v1/upload/task/b2b/wholesale
operation_id: postV1UploadTaskB2bWholesale
tags:
  - Цены и скидки
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 3df991d237cf1311
---

# Установить оптовые скидки для B2B-продаж{{ /api/discounts-prices/v1/upload/task/b2b/wholesale }}

`POST /api/discounts-prices/v1/upload/task/b2b/wholesale`

Описание метода Метод доступен по Персональному токену, Сервисному токену Метод устанавливает [оптовые скидки для бизнеса](https://seller.wildberries.ru/instructions/ru/ru/material/how-to-enable-wholesale-discounts-for-business) Получить информацию о процессе установки цен и скидок можно с помощью методов состояния и детализации обработанной загрузки. Лимит запросов на один аккаунт продавца для всех методов категории Цены и скидки : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 6 сек | 10 запросов | 600 мс | 5 запросов | | Сервисный | 6 сек | 10 запросов | 600 мс | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `data` — array[object] **обязательный**. Товары и оптовые скидки для B2B
  - `nmId` — integer **обязательный**. Артикул WB
  - `wholesaleDiscountThreshold` — array[object] **обязательный**. Оптовые скидки разных уровней для B2B
    - `minQuantity` — integer **обязательный**. Минимальное количество единиц товара для скидки
    - `wholesaleDiscount` — integer **обязательный**. Скидка, %. Чтобы удалить скидку, укажите `0`. Такой запрос одновременно удалит скидки на этом уровне и на всех более высоких уровнях `level` — вне зависимости от указания их в запросе
    - `level` — integer **обязательный**. Уровень скидки

## Ответы

**200** — Успешно

- `id` — integer **обязательный**. ID загрузки
- `alreadyExists` — boolean **обязательный**. Дублирование загрузки: `true` — такая загрузка уже есть
- `results` — array[object] **обязательный**. Результаты обработки запроса
  - `nmId` — integer **обязательный**. Артикул WB
  - `success` — boolean **обязательный**. Успешна ли установка скидки на товар: - `false` — неуспешна - `true` — успешна
  - `error` — object. Ошибка. При `"success":false`
    - `status` — integer **обязательный**. HTTP статус-код
    - `title` — string **обязательный**. Заголовок ошибки
    - `detail` — string **обязательный**. Детали ошибки

**208** — Такая загрузка уже есть

- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ответа
- `detail` — string **обязательный**. Детали ответа
- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

**400** — Неправильный запрос

- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. ID внутреннего сервиса WB

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
