---
title: Список отзывов{{ /api/v1/feedbacks }}
api: wb-user-communication
method: GET
path: /api/v1/feedbacks
operation_id: getV1Feedbacks
tags:
  - feedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 603f12ca37966ef3
---

# Список отзывов{{ /api/v1/feedbacks }}

`GET /api/v1/feedbacks`

Описание метода Метод возвращает список отзывов по заданным фильтрам. Вы можете: - получить данные обработанных и необработанных отзывов. Отзыв считается обработанным, если выполняется одно из условий: - на отзыв получен ответ - отзыв содержит только оценку (без текста и фото) - сортировать отзывы по дате - настроить пагинацию и количество отзывов в ответе Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов | | Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов | | Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов | | Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `isAnswered` | query | boolean | да | Вернуть только обработанные отзывы: - `true` — да - `false` — нет |
| `nmId` | query | integer | нет | Артикул WB |
| `take` | query | integer | да | Количество отзывов (max. 5 000) |
| `skip` | query | integer | да | Количество отзывов для пропуска (max. 199990) |
| `order` | query | string (dateAsc, dateDesc) | нет | Сортировка отзывов по дате (dateAsc/dateDesc) |
| `dateFrom` | query | integer | нет | Дата начала периода в формате Unix timestamp |
| `dateTo` | query | integer | нет | Дата конца периода в формате Unix timestamp |

## Ответы

**200** — Успешно

- `data` — object
  - `countUnanswered` — integer. Количество необработанных отзывов
  - `countArchive` — integer. Количество обработанных отзывов
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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
