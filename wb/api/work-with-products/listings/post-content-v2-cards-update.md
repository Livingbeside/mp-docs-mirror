---
title: Редактирование карточек товаров
api: wb-work-with-products
method: POST
path: /content/v2/cards/update
operation_id: post-content-v2-cards-update
tags:
  - listings
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: e3828a0c8214b7fa
---

# Редактирование карточек товаров

`POST /content/v2/cards/update`

Описание метода

Метод обновляет данные карточек товаров. Также используйте его, чтобы добавлять новые размеры.

 Карточка товара перезаписывается при обновлении. Поэтому в запросе нужно передать в том числе те параметры карточки, которые вы не собираетесь обновлять. Их значения можно получить в [списке карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post) и [списке карточек товаров в корзине](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1trash/post).

С помощью этого метода нельзя обновлять или удалять:
 - баркоды размеров товара. Можно только добавить дополнительные баркоды
 - параметры `photos`, `video` и `tags`
 - цены товаров. Цену можно задать, только если вы добавляете новые размеры

При добавлении нового размера укажите его цену через параметр `price`. Если в запросе не указан `price`, цена размера будет `0` — в этом случае изменить её можно будет с помощью методов:
 - [Установить цены и скидки](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1upload~1task/post), если у [товара](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1list~1goods~1filter/get) `"editablePriceSize":false`
 - [Установить цены для размеров](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1upload~1task~1size/post), если у [товара](./work-with-products#tag/Ceny-i-skidki/paths/~1api~1v2~1list~1goods~1filter/get) `"editablePriceSize":true`

Габариты товаров можно указать только в `сантиметрах`, вес товара с упаковкой — в `килограммах`.

Одним запросом можно отредактировать максимум 3000 карточек товаров (`nmID`). Максимальный размер запроса 10 Мб.

Если ответ `Успешно` (`200`), но какие-то карточки не обновились, проверьте [список несозданных карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1cards~1error~1list/post).

Синхронизация данных с сервисами может занимать до 30 минут. В течение этого времени невозможно добавить остатки на склады и настроить цены. 

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 10 запросов | 6 сек | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `brand` — string. Бренд
- `characteristics` — array[object]. Характеристики товара. Можно получить методом [Характеристики предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1charcs~1%7BsubjectId%7D/get)
  - `id` — integer **обязательный**. ID характеристики
  - `value` — ? **обязательный**. Значения характеристики. Тип данных — массив строк или число — зависит от типа характеристики, см. описание поля `charcType` в методе [Характеристики предмета](./work-with-products#tag/categoriesSubcategoriesAndCharacteristics/paths/~1content~1v2~1object~1charcs~1%7BsubjectId%7D/get). Допустимое количество значений отображено в поле `maxCount` того же метода
- `description` — string. Описание товара. Максимальное количество символов зависит от категории товара Стандарт — 2000, минимум — 1000, максимум — 5000 Подробно о **правилах заполнения карточки товара** в [Справочном центре](https://seller.wildberries.ru/instructions/ru/ru/material/how-to-create-card) на портале продавцов
- `dimensions` — object. Габариты и вес товара **c упаковкой**. Укажите в `сантиметрах` и `килограммах` для любого товара. Синхронизация новых данных с сервисом может занимать до 30 минут
  - `height` — integer. Высота, см
  - `length` — integer. Длина, см
  - `weightBrutto` — number. Вес, кг Количество знаков после запятой <=3
  - `width` — integer. Ширина, см
- `kizMarked` — boolean. Подтверждение, что на товар нанесён обязательный код маркировки [Честного знака](https://честныйзнак.рф/): - `true` — продавец подтверждает, что на товар нанесён обязательный код маркировки. - `false` — продавец подтверждает, что на товар нанесён обязательный код маркировки. Передайте в запросе `true`, чтобы подтвердить наличие на товаре обязательного кода маркировки. Карточка товара не пройдёт модерацию, если нет подтверждения продавца о том, что обязательный код маркировки нанесён на товар. Чтобы проверить, является ли код маркировки [Честного знака](https://честныйзнак.рф/) обязательным, используйте метод [Список карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post), поле ответа `needKiz` По умолчанию: `False`.
- `nmID` — integer **обязательный**. Артикул WB
- `sizes` — array[object] **обязательный**. Массив размеров Для безразмерного товара всё равно нужно передавать данный массив без параметров (wbSize и techSize), но с баркодом
  - `chrtID` — integer. ID размера для данного артикула WB Обязателен к заполнению для существующих размеров Для добавляемых размеров не указывается
  - `price` — integer. Цена товара, ₽ Указывается при добавлении размера
  - `skus` — array[string]. Баркоды
  - `techSize` — string. Размер товара (например, XL, S, 45)
  - `wbSize` — string. Российский размер товара
- `title` — string. Наименование товара
- `vendorCode` — string **обязательный**. Артикул продавца

## Ответы

**200** — Успешно

- `additionalErrors` — object | string. Дополнительные ошибки
  - `string` — string
  - `error` — string **обязательный**
- `data` — object. Данные ответа
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки

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

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `additionalErrors` — string. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**413** — Превышен лимит объёма данных в запросе

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
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
