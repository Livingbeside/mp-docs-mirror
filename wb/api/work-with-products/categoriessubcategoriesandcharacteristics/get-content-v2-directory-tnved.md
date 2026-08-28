---
title: ТНВЭД-код
api: wb-work-with-products
method: GET
path: /content/v2/directory/tnved
operation_id: get-content-v2-directory-tnved
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: dee5901be6e01b18
---

# ТНВЭД-код

`GET /content/v2/directory/tnved`

Описание метода

Метод возвращает список ТНВЭД-кодов по ID [предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1all/get) и фрагменту ТНВЭД-кода.

Лимит запросов на один аккаунт продавца для всех методов категории Контент:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 100 запросов | 600 мс | 5 запросов |

Исключение — методы:

 [создания карточек товаров](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post)

 [создания карточек товаров с присоединением](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload~1add/post)

 [редактирования карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post)

 [восстановления карточек товаров из корзины](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1recover/post)

 [получения списка рекомендаций в карточках товаров](./work-with-products#tag/recommendations/operation/postV1RecommendationsList)

 [установки рекомендаций для товаров](./work-with-products#tag/recommendations/operation/postV1RecommendationsSet)

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `subjectID` | query | integer | да | ID предмета |
| `search` | query | integer | нет | Поиск по ТНВЭД-коду. Работает только в паре с `subjectID` |
| `locale` | query | string | нет | Язык полей ответа: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |

## Ответы

**200** — Успешно

- `additionalErrors` — string. Дополнительные ошибки
- `data` — array[object]. Данные
  - `isKiz` — boolean. - `true` — код маркировки [Честного знака](https://честныйзнак.рф/) требуется - `false` — код маркировки [Честного знака](https://честныйзнак.рф/) не требуется
  - `tnved` — string. ТНВЭД-код
- `error` — boolean. Флаг наличия ошибки
- `errorText` — string. Текст ошибки

**400** — Неправильный запрос

- `additionalErrors` — object. Дополнительные ошибки
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

**403** — Доступ запрещён

- `additionalErrors` — string. Дополнительные ошибки
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
