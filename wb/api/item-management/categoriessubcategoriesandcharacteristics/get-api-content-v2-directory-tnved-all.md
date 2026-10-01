---
title: Список кодов ТН ВЭД
api: wb-item-management
method: GET
path: /api/content/v2/directory/tnved/all
operation_id: getV2DirectoryTnvedAll
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 071e1b3a46e7e057
---

# Список кодов ТН ВЭД

`GET /api/content/v2/directory/tnved/all`

Описание метода

Метод возвращает справочный список всех кодов ТН ВЭД. Чтобы найти код по его фрагменту, укажите первые цифры кода в параметре `search`.

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
| `search` | query | integer | нет | Поиск по первым цифрам кода ТН ВЭД. Укажите не более 10 символов |
| `locale` | query | string (ru, en) | нет | Язык полей ответа: - `ru` — русский - `en` — английский |

## Ответы

**200** — Успешно

- `data` — array[object] **обязательный**. Данные
  - `tnved` — string **обязательный**. Код ТН ВЭД
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
