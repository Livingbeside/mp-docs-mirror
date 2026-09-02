---
title: Характеристики предмета{{ /content/v2/object/charcs/{subjectId} }}
api: wb-item-management
method: GET
path: /content/v2/object/charcs/{subjectId}
operation_id: get-content-v2-object-charcs-subjectid
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 3adf4d2a371e4915
---

# Характеристики предмета{{ /content/v2/object/charcs/{subjectId} }}

`GET /content/v2/object/charcs/{subjectId}`

Описание метода

Метод возвращает параметры характеристик предмета: названия, типы данных, единицы измерения и так далее. В запросе необходимо указать ID [предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1all/get).

 Для получения значений характеристик [Цвет](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1directory~1colors/get), [Пол](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1directory~1kinds/get), [Страна производства](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1directory~1countries/get), [Сезон](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1directory~1seasons/get), [Ставка НДС](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1directory~1vat/get) и [ТНВЭД-код](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1directory~1tnved/get) используйте отдельные методы

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
| `subjectId` | path | integer | да | ID предмета |
| `locale` | query | string | нет | Язык полей ответа `subjectName` и `name`: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |

## Ответы

**200** — Успешно

- `data` — array[object]. Данные
  - `charcID` — integer. ID характеристики
  - `subjectName` — string. Название предмета
  - `subjectID` — integer. ID предмета
  - `name` — string. Название характеристики
  - `required` — boolean. - `true` — характеристику необходимо обязательно указать в карточке товара - `false` — характеристику необязательно указывать
  - `unitName` — string. Единица измерения
  - `maxCount` — integer. Максимальное количество значений, которое можно присвоить характеристике при [создании](./work-with-products#tag/listingItems) или [редактировании](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post) карточек товаров. Используется только для характеристик с `"charcType":1` — массив строк. Характеристикам с `"charcType":4` — число, можно присвоить только одно значение. Если `"maxCount":0`, количество значений не ограничено
  - `popular` — boolean. Характеристика популярна у пользователей (true - да, false - нет)
  - `charcType` — integer. Тип данных характеристики, который необходимо использовать при [создании](./work-with-products#tag/listingItems) или [редактировании](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post) карточек товаров: - `1` — массив строк - `4` — число (целое либо с десятичной дробью) - `0` — характеристика не используется
  - `hasFilter` — boolean. Ключевая характеристика. Является ли характеристика значимой для покупателей: - `true` — да - `false` — нет
  - `isVariable` — boolean. Признак [меняющейся характеристики](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov). Значение размечает характеристики, по которым варианты отличаются друг от друга: - `true` — варианты товара отличаются по этой характеристике - `false` — варианты товара не отличаются по этой характеристике
  - `existNamedField` — boolean. Как передать характеристику в запросах на [cоздание](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload/post), [создание с присоединением](./work-with-products#tag/listingItems/paths/~1content~1v2~1cards~1upload~1add/post) и [редактирование](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1update/post) карточек товара: - `true` — в соответствующем параметре запроса - `false` — внутри массива `characteristics`
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
