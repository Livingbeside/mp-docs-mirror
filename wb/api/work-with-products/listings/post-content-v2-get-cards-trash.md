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
content_sha: 89aaa4433170091a
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
  - `cursor` — object. Пагинатор
    - `limit` — integer. Сколько карточек товаров выдать в ответе По умолчанию: `10`.
    - `nmID` — integer. Артикул WB, с которого надо запрашивать следующий список карточек товаров
    - `trashedAt` — string. Дата и время помещения в корзину
  - `filter` — object. Параметры фильтрации
    - `textSearch` — string. Поиск по артикулу продавца, артикулу WB, баркоду
  - `sort` — object. Параметр сортировки
    - `ascending` — boolean. Сортировать по `trashedAt`: - `false` — по убыванию - `true` — по возрастанию По умолчанию: `False`.

## Ответы

**200** — Успешно

- `cards` — array[object]. Массив карточек товаров
  - `characteristics` — array[object]. Характеристики
    - `id` — integer. ID характеристики
    - `name` — string. Название характеристики
    - `value` — ?. Значение характеристики. Тип значения зависит от типа характеристики
  - `createdAt` — string. Date and time the item was listed
  - `dimensions` — object. Габариты и вес товара c упаковкой, см и кг
    - `height` — integer. Высота, см
    - `isValid` — boolean. Потенциальная некорректность габаритов товара: - `true` — не выявлена. `"isValid":true` не гарантирует, что размеры указаны корректно. В отдельных случаях (например, при создании новой категории товаров) `"isValid":true` будет возвращаться при любых значениях, кроме нулевых. - `false` — указанные габариты значительно отличаются от средних по категории (предмету). Рекомендуется перепроверить, правильно ли указаны размеры товара в упаковке в `сантиметрах`. Функциональность карточки товара, в том числе начисление логистики и хранения, при этом ограничена не будет. Логистика и хранение продолжают начисляться — по текущим габаритам. Также `"isValid":false` возвращается при отсутствии значений или нулевом значении любой стороны.
    - `length` — integer. Длина, см
    - `weightBrutto` — number. Вес, кг Количество знаков после запятой <=3
    - `width` — integer. Ширина, см
  - `kizMarked` — boolean. Есть ли подтверждение от продавца, что обязательный код маркировки [Честного знака](https://честныйзнак.рф/) нанесён на товар: - `true` — да - `false` — нет Чтобы проверить, является ли код маркировки [Честного знака](https://честныйзнак.рф/) обязательным, используйте метод [Список карточек товаров](./work-with-products#tag/listings/paths/~1content~1v2~1get~1cards~1list/post), поле ответа `needKiz` По умолчанию: `False`.
  - `nmID` — integer. Артикул WB
  - `photos` — array[object]. Массив фото
    - `big` — string. URL фото `900x1200`
    - `c246x328` — string. URL фото `248x328`
    - `c516x688` — string. URL фото `516x688`
    - `square` — string. URL фото `600x600`
    - `tm` — string. URL фото `75x100`
  - `sizes` — array[object]. Массив размеров
    - `chrtID` — integer. ID размера
    - `skus` — array[string]. Массив баркодов
    - `techSize` — string. Размер товара
    - `wbSize` — string. Российский размер товара
  - `subjectID` — integer. ID предмета
  - `subjectName` — string. Название предмета
  - `trashedAt` — string. Дата и время помещения в корзину
  - `vendorCode` — string. Артикул продавца
  - `video` — string. URL видео
  - `wholesale` — object. Оптовая продажа
    - `enabled` — boolean. Предназначена ли карточка товара для оптовой продажи
    - `quantum` — number<uint64>. Количество единиц товара в упаковке
- `cursor` — object. Пагинатор
  - `nmID` — integer. Артикул WB, с которого надо запрашивать следующий список карточек товаров
  - `total` — integer. Количество возвращённых карточек товаров
  - `trashedAt` — string. Дата и время, с которых надо запрашивать следующий список карточек товаров

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

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
