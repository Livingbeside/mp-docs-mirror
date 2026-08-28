---
title: Список предметов
api: wb-work-with-products
method: GET
path: /content/v2/object/all
operation_id: get-content-v2-object-all
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: c77af2b6f3ebb66b
---

# Список предметов

`GET /content/v2/object/all`

Описание метода

Метод возвращает список названий [родительских категорий предметов](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1parent~1all/get) и их предметов с ID. Например, у категории `Игрушки` будут предметы `Калейдоскопы`, `Куклы`, `Мячики`.

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
| `locale` | query | string | нет | Язык полей ответа: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |
| `name` | query | string | нет | Поиск по названию предмета (Носки), поиск работает по подстроке, искать можно на любом из поддерживаемых языков |
| `limit` | query | integer | нет | Количество предметов, максимум 1000 |
| `offset` | query | integer | нет | Сколько элементов пропустить. Например, для значения `10` ответ начнется с 11 элемента |
| `parentID` | query | integer | нет | ID родительской категории предмета |

## Ответы

**200** — Успешно

- `additionalErrors` — string. Дополнительные ошибки
- `data` — array[object]. Предметы
  - `parentID` — integer. ID родительской категории
  - `parentName` — string. Название родительской категории
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета
- `error` — boolean. Флаг наличия ошибки
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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
