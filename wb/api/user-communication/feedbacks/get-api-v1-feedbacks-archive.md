---
title: Список архивных отзывов
api: wb-user-communication
method: GET
path: /api/v1/feedbacks/archive
operation_id: getV1FeedbacksArchive
tags:
  - feedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 01dda527ea008ea7
---

# Список архивных отзывов

`GET /api/v1/feedbacks/archive`

Описание метода

Метод возвращает список архивных [отзывов](./user-communication#tag/feedbacks/operation/getV1Feedbacks).

Отзыв становится архивным, если:
 - на отзыв получен ответ
 - на отзыв не получен ответ в течение 30 дней
 - в отзыве нет текста и фото

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
| `nmId` | query | integer | нет | Артикул WB |
| `take` | query | integer | да | Количество отзывов (max. 5 000) |
| `skip` | query | integer | да | Количество отзывов для пропуска |
| `order` | query | string (dateAsc, dateDesc) | нет | Сортировка отзывов по дате (dateAsc/dateDesc) |

## Ответы

**200** — Успешно

- `data` — object
  - `feedbacks` — array[object]. Массив отзывов
    - `id` — string. ID отзыва
    - `text` — string. Текст отзыва
    - `pros` — string. Достоинства товара
    - `cons` — string. Недостатки товара
    - `productValuation` — integer. Оценка товара
    - `createdDate` — string<date-time>. Дата и время создания отзыва
    - `answer` — object. Структура ответа
      - `text` — string. Текст ответа
      - `state` — string. Статус: - `none` — новый - `wbRu` — отображается на сайте - `reviewRequired` — ответ проходит проверку - `rejected` — ответ отклонён
      - `editable` — boolean. Можно ли отредактировать ответ: - `false` — нет - `true` — да
    - `state` — string. Статус отзыва: - `none` - не обработан (новый) - `wbRu` - обработан
    - `productDetails` — object. Информация о товаре
      - `nmId` — integer. Артикул WB
      - `imtId` — integer. ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
      - `productName` — string. Название товара
      - `supplierArticle` — string. Артикул продавца
      - `supplierName` — string. Имя продавца
      - `brandName` — string. Бренд товара
      - `size` — string. Размер товара (`techSize` в КТ)
    - `photoLinks` — array[object]. Массив структур фотографий
      - `fullSize` — string. Адрес фотографии полного размера
      - `miniSize` — string. Адрес фотографии маленького размера
    - `video` — object. Структура видео
      - `previewImage` — string. Ссылка на обложку видео
      - `link` — string. Ссылка на файл плейлиста видео (доступно по протоколу HLS)
      - `durationSec` — integer. Общая продолжительность видео
    - `wasViewed` — boolean. Просмотрен ли отзыв
    - `userName` — string. Имя автора отзыва
    - `orderStatus` — string. Статус заказа. Возможные значения: - `buyout` — выкуплен - `rejected` — отказались - `returned` — возврат - `notSpecified` — статус не присвоен
    - `matchingSize` — string. Соответствие заявленного размера реальному. Возможные значения: - ` ` — для безразмерных товаров - `ок` — соответствует размеру - `smaller` — маломерит - `bigger` — большемерит
    - `isAbleSupplierFeedbackValuation` — boolean. Доступна ли продавцу возможность оставить жалобу на отзыв (`true` — доступна, `false` — не доступна)
    - `supplierFeedbackValuation` — integer. Ключ причины жалобы на отзыв
    - `isAbleSupplierProductValuation` — boolean. Доступна ли продавцу возможность сообщить о проблеме с товаром: - `true` — да - `false` — нет
    - `supplierProductValuation` — integer. Ключ проблемы с товаром
    - `isAbleReturnProductOrders` — boolean. Опция возврата товара: - `true` — доступна - `false` — недоступна
    - `returnProductOrdersDate` — string. Дата и время, когда на запрос возврата был получен ответ со статус-кодом 200.
    - `bables` — array[string]. Список тегов покупателя
    - `lastOrderShkId` — integer. Штрихкод единицы товара
    - `lastOrderCreatedAt` — string. Дата покупки
    - `color` — string. Цвет товара
    - `subjectId` — integer. ID предмета
    - `subjectName` — string. Название предмета
    - `parentFeedbackId` — string. ID начального отзыва (`null`, если этот отзыв начальный)
    - `childFeedbackId` — string. ID дополненного отзыва (`null`, если этот отзыв дополненный)
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки

**400** — Неправильный запрос

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

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

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

**422** — Ошибка обработки параметров запроса

- `data` — object
- `error` — boolean. Есть ли ошибка
- `errorText` — string. Описание ошибки
- `additionalErrors` — array[string]. Дополнительные ошибки
- `requestId` — string

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
