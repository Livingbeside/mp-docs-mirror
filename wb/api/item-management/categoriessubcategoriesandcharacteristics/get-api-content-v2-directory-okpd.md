---
title: Код ОКПД2 предмета
api: wb-item-management
method: GET
path: /api/content/v2/directory/okpd
operation_id: getV2DirectoryOkpd
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 18f4c2ffc328d026
---

# Код ОКПД2 предмета

`GET /api/content/v2/directory/okpd`

Описание метода

Метод возвращает список кодов ОКПД2 по ID [предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1all/get) и фрагменту кода ОКПД2.

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

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `subjectId` | query | integer | да | ID предмета |
| `search` | query | string | нет | Поиск по фрагменту кода ОКПД2. Работает только в паре с `subjectId`. Укажите первые цифры кода через точку, чтобы найти код по этому фрагменту |
| `locale` | query | string (ru) | нет | Язык полей ответа: - `ru` — русский |

## Ответы

**200** — Успешно

- `data` — array[object] **обязательный**. Данные
  - `okpd2` — string **обязательный**. Код ОКПД2
  - `description` — string **обязательный**. Текстовое описание товаров, которые входят в группу
- `error` — boolean **обязательный**. Флаг наличия ошибки
- `errorText` — string **обязательный**. Текст ошибки
- `additionalErrors` — string **обязательный**. Дополнительные ошибки

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
