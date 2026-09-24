---
title: Установить цены и скидки
api: wb-item-management
method: POST
path: /api/v2/upload/task
operation_id: postV2UploadTask
tags:
  - pricesAndDiscounts
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 6a73710079c50590
---

# Установить цены и скидки

`POST /api/v2/upload/task`

Описание метода

Метод устанавливает цены и скидки для товаров.

Чтобы установить цены для размеров товара, используйте [отдельный метод](./item-management#tag/pricesAndDiscounts/operation/postV2UploadTaskSize).

 Получить информацию о процессе установки цен и скидок можно с помощью методов [состояния](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryTasks) и [детализации](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask) обработанной загрузки.

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

- `data` — array[object] **обязательный**. Товары, цены и скидки для них. Максимум 1 000 товаров. Цена и скидка не могут быть пустыми одновременно. Если новая цена товара со скидкой будет меньше [порогового значения](https://seller.wildberries.ru/instructions/ru/ru/material/price-quarantine#2ef3641a-5165-41db-9ac7-e4374c9fc3f1), товар попадёт в [карантин](https://seller.wildberries.ru/instructions/ru/ru/material/price-quarantine) и будет продаваться по старой цене. Ошибка об этом будет в [детализации загрузки](./item-management#tag/pricesAndDiscounts/operation/getV2HistoryGoodsTask). Вы можете изменить цену или скидку с помощью API либо вывести товар из карантина в [личном кабинете](https://seller.wildberries.ru/discount-and-prices/quarantine)
  - `nmID` — integer **обязательный**. Артикул WB
  - `price` — integer. Цена. Валюту можно получить с помощью методов [Получить товары с ценами](./item-management#tag/pricesAndDiscounts/operation/getV2ListGoodsFilter) и [Получить товары с ценами по артикулам](./item-management#tag/pricesAndDiscounts/operation/postV2ListGoodsFilter), поле `currencyIsoCode4217`
  - `discount` — integer. Скидка, %

## Ответы

**200** — Успешно

- `data` — object. Данные ответа
  - `id` — integer. ID загрузки
  - `alreadyExists` — boolean. Флаг дублирования загрузки: `true` — такая загрузка уже есть
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**208** — Такая загрузка уже есть

- `data` — object. Данные ответа
  - `id` — integer. ID загрузки
  - `alreadyExists` — boolean. Флаг дублирования загрузки: `true` — такая загрузка уже есть
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

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

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**409** — Ошибка при конвертации валюты

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**422** — Неожидаемый результат

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
