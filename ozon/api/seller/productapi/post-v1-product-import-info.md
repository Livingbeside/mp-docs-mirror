---
title: Узнать статус добавления или обновления товара
api: ozon-seller
method: POST
path: /v1/product/import/info
operation_id: ProductAPI_GetImportProductsInfo
tags:
  - ProductAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 92b4076b91c11a47
---

# Узнать статус добавления или обновления товара

`POST /v1/product/import/info`

Позволяет получить статус создания или обновления карточки товара. Если вы обновили изображение или видео по ссылке, но ссылка не изменилась, для изображения или видео в параметре `result.items.status` вернётся `skipped`.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `task_id` — integer<int64> **обязательный**. Код задачи на импорт товаров. Можно получить с помощью метода [/v3/product/import](#operation/ProductAPI_ImportProductsV3).

## Ответы

**200** — Статус добавления или обновления товара

- `result` — object
  - `items` — array[object]. Информация о товарах.
    - `offer_id` — string. Идентификатор товара в системе продавца — артикул. Максимальная длина строки в значении поля — 50 символов.
    - `product_id` — integer<int64>. Идентификатор товара в системе Ozon — `product_id`.
    - `status` — string. Статус создания или обновления товара. Информация о товаре обрабатывается очередями. Возможные значения параметра: - `pending` — товар в очереди на обработку; - `imported` — товар успешно загружен; - `failed` — товар загружен с ошибками; - `skipped` — товар не был обновлен, так как запрос не содержал изменений.
    - `errors` — array[object]. Массив ошибок.
      - `code` — string. Код ошибки.
      - `message` — string. Техническое описание ошибки.
      - `state` — string. Состояние товара, в котором произошла ошибка.
      - `level` — string. Уровень ошибки.
      - `description` — string. Описание ошибки.
      - `field` — string. Поле, в котором произошла ошибка.
      - `attribute_id` — integer<int64>. Атрибут, в котором произошла ошибка.
      - `attribute_name` — string. Название атрибута, в котором произошла ошибка.
  - `total` — integer<int32>. Идентификатор товара в системе продавца — артикул.

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
