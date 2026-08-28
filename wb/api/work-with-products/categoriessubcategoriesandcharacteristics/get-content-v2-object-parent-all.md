---
title: Родительские категории товаров{{ /content/v2/object/parent/all }}
api: wb-work-with-products
method: GET
path: /content/v2/object/parent/all
operation_id: get-content-v2-object-parent-all
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: a780a076d11fa25a
---

# Родительские категории товаров{{ /content/v2/object/parent/all }}

`GET /content/v2/object/parent/all`

Описание метода Метод возвращает названия и ID всех родительских категорий для [создания карточек товаров](./work-with-products#tag/listingItems): например, `Электроника`, `Бытовая химия`, `Рукоделие`. Лимит запросов на один аккаунт продавца для всех методов категории Контент : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 100 запросов | 600 мс | 5 запросов | Исключение — методы: создания карточек товаров создания карточек товаров с присоединением редактирования карточек товаров восстановления карточек товаров из корзины получения списка рекомендаций в карточках товаров установки рекомендаций для товаров В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string | нет | Язык поля ответа `name`: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |

## Ответы

**200** — Успешно

- `data` — ?
  - `name` — string. Название категории
  - `id` — integer. ID родительской категории
  - `isVisible` — boolean. Виден на сайте
- `error` — boolean. Флаг наличия ошибки
- `errorText` — string. Описание ошибки
- `additionalErrors` — string. Дополнительные ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки
- `additionalErrors` — object. Дополнительные ошибки

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

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки
- `additionalErrors` — string. Дополнительные ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
