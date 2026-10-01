---
title: Список кодов ОКПД2
api: wb-item-management
method: GET
path: /api/content/v2/directory/okpd/all
operation_id: getV2DirectoryOkpdAll
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 95a888b99bd75ccc
---

# Список кодов ОКПД2

`GET /api/content/v2/directory/okpd/all`

Описание метода

Метод возвращает справочный список всех кодов ОКПД2. Чтобы найти код по его фрагменту, укажите первые цифры кода через точку в параметре `search`.

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
| `search` | query | number | нет | Поиск по фрагменту кода ОКПД2. Укажите первые цифры кода через точку, чтобы найти код по этому фрагменту |
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
