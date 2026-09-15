---
title: Характеристики предмета{{ /content/v2/object/charcs/{subjectId} }}
api: wb-item-management
method: GET
path: /content/v2/object/charcs/{subjectId}
operation_id: getV2ObjectCharcsSubjectId
tags:
  - categoriesSubcategoriesAndCharacteristics
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/item-management"
deprecated: false
content_sha: 73fa1694d7a5f169
---

# Характеристики предмета{{ /content/v2/object/charcs/{subjectId} }}

`GET /content/v2/object/charcs/{subjectId}`

Описание метода

Метод возвращает параметры характеристик предмета: названия, типы данных, единицы измерения и так далее. В запросе необходимо указать ID [предмета](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2ObjectAll).

 Для получения значений характеристик [Цвет](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryColors), [Пол](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryKinds), [Страна производства](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryCountries), [Сезон](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectorySeasons), [Ставка НДС](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryVat) и [ТНВЭД-код](./item-management#tag/categoriesSubcategoriesAndCharacteristics/operation/getV2DirectoryTnved) используйте отдельные методы

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
  - `maxCount` — integer. Максимальное количество значений, которое можно присвоить характеристике при [создании](./item-management#tag/listingItems) или [редактировании](./item-management#tag/listings/operation/postV2CardsUpdate) карточек товаров. Используется только для характеристик с `"charcType":1` — массив строк. Характеристикам с `"charcType":4` — число, можно присвоить только одно значение. Если `"maxCount":0`, количество значений не ограничено
  - `popular` — boolean. Характеристика популярна у пользователей (true - да, false - нет)
  - `charcType` — integer. Тип данных характеристики, который необходимо использовать при [создании](./item-management#tag/listingItems) или [редактировании](./item-management#tag/listings/operation/postV2CardsUpdate) карточек товаров: - `1` — массив строк - `4` — число (целое либо с десятичной дробью) - `0` — характеристика не используется
  - `hasFilter` — boolean. Ключевая характеристика. Является ли характеристика значимой для покупателей: - `true` — да - `false` — нет
  - `isVariable` — boolean. Признак [меняющейся характеристики](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov). Значение размечает характеристики, по которым варианты отличаются друг от друга: - `true` — варианты товара отличаются по этой характеристике - `false` — варианты товара не отличаются по этой характеристике
  - `existNamedField` — boolean. Как передать характеристику в запросах на [cоздание](./item-management#tag/listingItems/operation/postV2CardsUpload), [создание с присоединением](./item-management#tag/listingItems/operation/postV2CardsUploadAdd) и [редактирование](./item-management#tag/listings/operation/postV2CardsUpdate) карточек товара: - `true` — в соответствующем параметре запроса - `false` — внутри массива `characteristics`
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
