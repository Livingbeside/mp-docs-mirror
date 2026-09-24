---
title: Получить список пунктов возврата для склада rFBS
api: ozon-seller
method: POST
path: /v1/warehouse/rfbs/return-point/list
operation_id: WarehouseRfbsReturnPointList
tags:
  - BetaMethod
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: 35112f4be83770a5
---

# Получить список пунктов возврата для склада rFBS

`POST /v1/warehouse/rfbs/return-point/list`

Используйте метод при создании и обновлении складов rFBS и rFBS Express.

Вы можете оставить обратную связь о работе метода в [комментариях](https://dev.ozon.ru/community/2369-Novyi-beta-metod-dlia-polucheniia-vozvratnykh-tochek-dlia-rfbs-ekspress/) в сообществе разработчиков Ozon for dev.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filters` — object **обязательный**. Фильтры для поиска пунктов возврата.
  - `address` — string. Адрес пункта возврата.
  - `coordinates` — object **обязательный**. Координаты склада.
    - `latitude` — number<double> **обязательный**. Широта.
    - `longitude` — number<double> **обязательный**. Долгота.
  - `country_code` — string **обязательный**. Код страны в формате ISO 2.
  - `ids` — array[string<int64>]. Идентификаторы пунктов возврата.
  - `types` — array[string (PVZ, PPZ)]. Тип пункта возврата: - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов.
  - `warehouse_id` — integer<int64>. Идентификатор склада. Передайте его, если нужно получить пункты возврата для обновления склада. Для нового склада передавать не нужно.
- `last_id` — integer<int64>. Идентификатор последнего значения на странице.
- `limit` — integer<int32> **обязательный**. Количество значений в ответе.

## Ответы

**200** — Список пунктов возврата

- `points` — array[object]. Список пунктов возврата.
  - `address` — string. Адрес пункта возврата.
  - `coordinates` — object. Координаты пункта возврата.
    - `latitude` — number<double>. Широта.
    - `longitude` — number<double>. Долгота.
  - `id` — integer<int64>. Идентификатор пункта возврата.
  - `name` — string. Название пункта возврата.
  - `type` — string (PVZ, PPZ). Тип пункта возврата: - `PVZ` — пункт выдачи заказов; - `PPZ` — пункт приёма заказов. По умолчанию: `PVZ`.
  - `utc_offset` — integer<int32>. Смещение часового пояса от UTC-0 в минутах.
  - `working_days` — array[object]. Рабочие дни пункта возврата.
    - `date` — string. Дата рабочего дня.
    - `day` — string (UNSPECIFIED, MONDAY, TUESDAY, WEDNESDAY, THURSDAY, FRIDAY, SATURDAY, SUNDAY). День недели: - `UNSPECIFIED` — не определён; - `MONDAY` — понедельник; - `TUESDAY` — вторник; - `WEDNESDAY` — среда; - `THURSDAY` — четверг; - `FRIDAY` — пятница; - `SATURDAY` — суббота; - `SUNDAY` — воскресенье. По умолчанию: `UNSPECIFIED`.
    - `from` — string. Время начала рабочего дня.
    - `to` — string. Время окончания рабочего дня.

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
