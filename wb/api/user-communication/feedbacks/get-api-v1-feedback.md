---
title: Получить отзыв по ID
api: wb-user-communication
method: GET
path: /api/v1/feedback
operation_id: getV1Feedback
tags:
  - feedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: d66a0905f6ac68f2
---

# Получить отзыв по ID

`GET /api/v1/feedback`

Описание метода

Метод возвращает данные [отзыва](./user-communication#tag/feedbacks/operation/getV1Feedbacks) по его ID.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | query | string | да | ID отзыва |

## Ответы

**200** — Успешно

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
  - `answer` — object. Структура ответа
    - `editable` — boolean. Можно ли отредактировать ответ: - `false` — нет - `true` — да
    - `state` — string. Статус: - `none` — новый - `wbRu`— отображается на сайте - `reviewRequired` — ответ проходит проверку - `rejected` — ответ отклонён
    - `text` — string. Текст ответа
  - `bables` — array[string]. Список тегов покупателя
  - `childFeedbackId` — string. ID дополненного отзыва (`null`, если этот отзыв дополненный)
  - `color` — string. Цвет товара
  - `cons` — string. Недостатки товара
  - `createdDate` — string<date-time>. Дата и время создания отзыва
  - `id` — string. ID отзыва
  - `isAbleReturnProductOrders` — boolean. Опция возврата товара: - `true` — доступна - `false` — недоступна
  - `isAbleSupplierFeedbackValuation` — boolean. Доступна ли продавцу возможность оставить жалобу на отзыв: - `true`— да - `false` — нет
  - `isAbleSupplierProductValuation` — boolean. Доступна ли продавцу возможность сообщить о проблеме с товаром (`true` - доступна, `false` - не доступна)
  - `lastOrderCreatedAt` — string. Дата покупки
  - `lastOrderShkId` — integer. Штрихкод единицы товара
  - `matchingSize` — string. Соответствие заявленного размера реальному. Возможные значения: - ` ` - для безразмерных товаров - `ок` - соответствует размеру - `smaller` - маломерит - `bigger` - большемерит
  - `orderStatus` — string. Статус заказа. Возможные значения: - `buyout` — выкуплен - `rejected` — отказались - `returned` — возврат - `notSpecified` — статус не присвоен
  - `parentFeedbackId` — string. ID начального отзыва (`null`, если этот отзыв начальный)
  - `photoLinks` — array[object]. Массив структур фотографий
    - `fullSize` — string. Адрес фотографии полного размера
    - `miniSize` — string. Адрес фотографии маленького размера
  - `productDetails` — object. Item information
    - `brandName` — string. Бренд товара
    - `imtId` — integer. ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
    - `nmId` — integer. Артикул WB
    - `productName` — string. Название товара
    - `size` — string. Размер товара (`techSize` в КТ)
    - `supplierArticle` — string. Артикул продавца
    - `supplierName` — string. Имя продавца
  - `productValuation` — integer. Оценка товара
  - `pros` — string. Достоинства товара
  - `returnProductOrdersDate` — string. Дата и время, когда на запрос возврата был получен ответ со статус-кодом 200.
  - `state` — string. Статус отзыва: - `none` - не обработан (новый) - `wbRu` - обработан
  - `subjectId` — integer. ID предмета
  - `subjectName` — string. Название предмета
  - `supplierFeedbackValuation` — integer. Ключ причины жалобы на отзыв
  - `supplierProductValuation` — integer. Ключ проблемы с товаром
  - `text` — string. Текст отзыва
  - `userName` — string. Имя автора отзыва
  - `video` — object. Структура видео
    - `durationSec` — integer. Общая продолжительность видео
    - `link` — string. Ссылка на файл плейлиста видео (доступно по протоколу hls)
    - `previewImage` — string. Ссылка на обложку видео
  - `wasViewed` — boolean. Просмотрен ли отзыв
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки

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

**422** — Ошибка обработки параметров запроса

- `additionalErrors` — array[string]. Дополнительные ошибки
- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `requestId` — string

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
