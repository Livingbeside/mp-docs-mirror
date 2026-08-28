---
title: ТНВЭД-код{{ /content/v2/directory/tnved }}
api: wb-work-with-products
method: GET
path: /content/v2/directory/tnved
operation_id: get-content-v2-directory-tnved
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 4204cf76d5ac4d72
---

# ТНВЭД-код{{ /content/v2/directory/tnved }}

`GET /content/v2/directory/tnved`

Описание метода Метод возвращает список ТНВЭД-кодов по ID [предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1all/get) и фрагменту ТНВЭД-кода. Лимит запросов на один аккаунт продавца для всех методов категории Контент : | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 100 запросов | 600 мс | 5 запросов | Исключение — методы: создания карточек товаров создания карточек товаров с присоединением редактирования карточек товаров восстановления карточек товаров из корзины получения списка рекомендаций в карточках товаров установки рекомендаций для товаров В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

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
- `errorText` — string. Текст ошибки
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
