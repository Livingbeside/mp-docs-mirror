---
title: Страна производства
api: wb-item-management
method: GET
path: /content/v2/directory/countries
operation_id: getV2DirectoryCountries
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 5949eab413bd927a
---

# Страна производства

`GET /content/v2/directory/countries`

Описание метода

Метод возвращает возможные значения [характеристики](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectCharcsSubjectId) предмета `Страна производства`.

Лимит запросов на один аккаунт продавца для всех методов категории Контент:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 100 запросов | 600 мс | 5 запросов |

Исключение — методы:

 [создания карточек товаров](./item-management#tag/listingItems/operation/postV2CardsUpload)

 [создания карточек товаров с присоединением](./item-management#tag/listingItems/operation/postV2CardsUploadAdd)

 [редактирования карточек товаров](./item-management#tag/listings/operation/postV2CardsUpdate)

 [восстановления карточек товаров из корзины](./item-management#tag/listings/operation/postV2CardsRecover)

 [получения списка рекомендаций в карточках товаров](./item-management#tag/recommendations/operation/postV1RecommendationsList)

 [установки рекомендаций для товаров](./item-management#tag/recommendations/operation/postV1RecommendationsSet)

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string | нет | Язык полей ответа `subjectName` и `name`: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |

## Ответы

**200** — Успешно

- `data` — ?
  - `id` — integer. ID страны
  - `name` — string. Значение характеристики Страны
  - `fullName` — string. Полное название страны
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
- `additionalErrors` — string. Дополнительные ошибки

**400** — Неправильный запрос

- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
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
- `errorText` — string. Описание ошибки
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
