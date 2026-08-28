---
title: Список карточек товаров в корзине
api: wb-work-with-products
method: POST
path: /content/v2/get/cards/trash
operation_id: post-content-v2-get-cards-trash
tags:
  - listings
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 6d3104683fa2680e
---

# Список карточек товаров в корзине

`POST /content/v2/get/cards/trash`

Описание метода

Метод возвращает список карточек товаров в корзине.

Чтобы получить **больше 100** карточек товаров, используйте пагинацию.
 1. Сделайте первый запрос: 

 
 {
 "settings": {
 "sort": {
 "ascending": true
 },
 "cursor": {
 "limit": 100
 }
 }
 }
 Чтобы получать только карточки товаров, которые были перенесены в корзину после выгрузки, используйте сортировку по возрастанию: `"sort":{"ascending":true}`.
 2. Скопируйте `"trashedAt":"***","nmID":***` из `cursor` ответа и вставьте в `cursor` запроса.
 3. Повторите запрос.
 4. Повторяйте пункты 2 и 3, пока значение `total` в ответе не станет меньше, чем значение `limit` в запросе. Это будет означать, что вы получили все карточки.

Чтобы получать только карточки товаров, которые были перенесены в корзину после предыдущей выгрузки данных:
 1. Сохраните поля `"cursor":{"trashedAt":"***","nmID":***}` из последнего ответа предыдущей выгрузки. При выгрузке используйте сортировку по возрастанию: `"sort":{"ascending":true}`.
 2. Укажите в первом запросе сохранённые поля `"cursor":{"trashedAt":"***","nmID":"***"}`. Продолжайте использовать сортировку по возрастанию.
 3. Сохраните поля `"cursor":{"trashedAt":"***","nmID":***}` из последнего ответа текущей выгрузки.

 
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
| `locale` | query | string (ru, en, zh) | нет | Язык полей ответа `name`, `value` и `object`: - `ru` — русский - `en` — английский - `zh` — китайский Не используется в песочнице. Данные песочницы возвращаются только на русском языке |

## Запрос

**Тело запроса** (`application/json`):

- `settings` — object. Настройки
  - `sort` — object. Параметр сортировки
    - `ascending` — boolean. Сортировать по `trashedAt`: - `false` — по убыванию - `true` — по возрастанию По умолчанию: `False`.
  - `cursor` — object. Пагинатор
    - `limit` — integer. Сколько карточек товаров выдать в ответе По умолчанию: `10`.
    - `trashedAt` — string. Дата и время помещения в корзину
    - `nmID` — integer. Артикул WB, с которого надо запрашивать следующий список карточек товаров
  - `filter` — object. Параметры фильтрации
    - `textSearch` — string. Поиск по артикулу продавца, артикулу WB, баркоду

## Ответы

**200** — Успешно

- `cards` — array[object]. Массив карточек товаров
  - `nmID` — integer. Артикул WB
  - `vendorCode` — string. Артикул продавца
  - `kizMarked` — boolean. Есть ли подтверждение от продавца, что обязательный код маркировки [Честного знака](https://честныйзнак.рф/) нанесён на товар: - `true` — да - `false` — нет Чтобы проверить, является ли код маркировки [Честного знака](https://честныйзнак.рф/) обязательным, используйте метод [Список карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post), поле ответа `needKiz` По умолчанию: `False`.
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета
  - `photos` — array[object]. Массив фото
    - `big` — string. URL фото `900x1200`
    - `c246x328` — string. URL фото `248x328`
    - `c516x688` — string. URL фото `516x688`
    - `square` — string. URL фото `600x600`
    - `tm` — string. URL фото `75x100`
  - `video` — string. URL видео
  - `wholesale` — object. Оптовая продажа
    - `enabled` — boolean. Предназначена ли карточка товара для оптовой продажи
    - `quantum` — number<uint64>. Количество единиц товара в упаковке
  - `sizes` — array[object]. Массив размеров
    - `chrtID` — integer. ID размера
    - `techSize` — string. Размер товара
    - `wbSize` — string. Российский размер товара
    - `skus` — array[string]. Массив баркодов
  - `dimensions` — object. Габариты и вес товара c упаковкой, см и кг
    - `length` — integer. Длина, см
    - `width` — integer. Ширина, см
    - `height` — integer. Высота, см
    - `weightBrutto` — number. Вес, кг Количество знаков после запятой <=3
    - `isValid` — boolean. Потенциальная некорректность габаритов товара: - `true` — не выявлена. `"isValid":true` не гарантирует, что размеры указаны корректно. В отдельных случаях (например, при создании новой категории товаров) `"isValid":true` будет возвращаться при любых значениях, кроме нулевых. - `false` — указанные габариты значительно отличаются от средних по категории (предмету). Рекомендуется перепроверить, правильно ли указаны размеры товара в упаковке в `сантиметрах`. Функциональность карточки товара, в том числе начисление логистики и хранения, при этом ограничена не будет. Логистика и хранение продолжают начисляться — по текущим габаритам. Также `"isValid":false` возвращается при отсутствии значений или нулевом значении любой стороны.
  - `characteristics` — array[object]. Характеристики
    - `id` — integer. ID характеристики
    - `name` — string. Название характеристики
    - `value` — ?. Значение характеристики. Тип значения зависит от типа характеристики
  - `createdAt` — string. Date and time the item was listed
  - `trashedAt` — string. Дата и время помещения в корзину
- `cursor` — object. Пагинатор
  - `trashedAt` — string. Дата и время, с которых надо запрашивать следующий список карточек товаров
  - `nmID` — integer. Артикул WB, с которого надо запрашивать следующий список карточек товаров
  - `total` — integer. Количество возвращённых карточек товаров

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

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

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
