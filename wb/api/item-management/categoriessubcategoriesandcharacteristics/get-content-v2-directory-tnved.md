---
title: ТНВЭД-код
api: wb-item-management
method: GET
path: /content/v2/directory/tnved
operation_id: getV2DirectoryTnved
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: d158362e7f73307e
---

# ТНВЭД-код

`GET /content/v2/directory/tnved`

Описание метода

Метод возвращает список ТНВЭД-кодов по ID [предмета](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectAll) и фрагменту ТНВЭД-кода.

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
| `subjectID` | query | integer | да | ID предмета |
| `search` | query | integer | нет | Поиск по ТНВЭД-коду. Работает только в паре с `subjectID` |
| `locale` | query | string | нет | Язык полей ответа: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |

## Ответы

**200** — Успешно

- `data` — array[object]. Данные
  - `tnved` — string. ТНВЭД-код
  - `isKiz` — boolean. - `true` — код маркировки [Честного знака](https://честныйзнак.рф/) требуется - `false` — код маркировки [Честного знака](https://честныйзнак.рф/) не требуется
- `error` — boolean. Флаг наличия ошибки
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
