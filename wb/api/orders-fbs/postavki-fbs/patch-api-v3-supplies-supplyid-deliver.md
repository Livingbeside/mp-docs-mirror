---
title: Передать поставку в доставку{{ /api/v3/supplies/{supplyId}/deliver }}
api: wb-orders-fbs
method: PATCH
path: /api/v3/supplies/{supplyId}/deliver
operation_id: patch-api-v3-supplies-supplyid-deliver
tags:
  - Поставки FBS
spec_version: order
source: "https://dev.wildberries.ru/docs/openapi/orders-fbs"
deprecated: false
content_sha: 3dbf18cd75a3ed38
---

# Передать поставку в доставку{{ /api/v3/supplies/{supplyId}/deliver }}

`PATCH /api/v3/supplies/{supplyId}/deliver`

Описание метода

Метод закрывает [поставку](./orders-fbs#tag/Postavki-FBS/paths/~1api~1v3~1supplies~1%7BsupplyId%7D/get) и переводит все [сборочные задания](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders/get) в ней в [статус](./orders-fbs#tag/Sborochnye-zadaniya-FBS/paths/~1api~1v3~1orders~1status/post) `complete` — в доставке. После закрытия поставки добавить новые сборочные задания к ней нельзя.

Если поставка не была передана в доставку, то при приёмке первого товара поставка автоматически закроется.

Передать поставку в доставку можно, только если в ней:
 - есть хотя бы одно сборочное задание
 - для всех сборочных заданий указана обязательная маркировка
 - маркировка всех сборочных заданий прошла проверку

Если поставка содержит сборочные задания с обязательным УИН, убедитесь, что вы заранее создали и загрузили спецификацию с договором на доставку. [ГИИС ДМДК](https://minfin.gov.ru/ru/perfomance/jewels/dmdk) требуется около 30 минут для обработки изменений в статусах УИН.

Лимит запросов на один аккаунт продавца для методов сборочных заданий, поставок, пропусков и настроек автовозврата FBS:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 300 запросов | 200 мс | 20 запросов |

Один запрос с кодами ответов 4XX учитывается как 10 запросов.

В песочнице — максимум 1 запрос в секунду суммарно для всех методов Маркетплейса.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `supplyId` | path | string | да | ID поставки |

## Ответы

**204** — Передано в доставку

**400** — Неправильный запрос

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

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

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**404** — Не найдено

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
- `message` — string. Описание ошибки

**409** — Ошибка закрытия поставки

- `code` — string. Код ошибки
- `data` — object. Дополнительные данные ошибки
  - `orders` — array[object]. Сборочные задания, идентификаторы маркировки которых не прошли или ещё не завершили проверку
    - `id` — integer. ID сборочного задания
    - `metaDetails` — array[object]. Информация об ошибках
      - `decision` — string. [Статус проверки](/knowledge-base/articles/019e9273-118b-7b69-a25a-ea1d756f05d9/rabota-s-markirovkoi-po-modeli-fbs): - `imei` - `pending` — Проверка маркировки продолжается. Дождитесь изменения статуса проверки - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `imeiInvalidFormat` — Неверный формат маркировки - `imeiAlreadySold` — Товар с этим IMEI уже продан - `uin` - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `pending` — Проверка маркировки продолжается. Дождитесь изменения статуса проверки - `uinInvalidFormat` — Неверный формат маркировки - `uinBadStatus` — Некорректный статус партии - `uinBadProcess` — Некорректная стадия обработки - `uinBadStatusAndBadProcess` — Некорректный статус партии. Некорректная стадия обработки - `uinNotFound` — Не найден в [ГИИС](https://minfin.gov.ru/ru/perfomance/jewels/dmdk). При получении этой ошибки убедитесь, что УИН: - указан в загруженной спецификации с договором на доставку. Если спецификация загружена более 30 минут назад, [удалите УИН](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta/delete) из сборочного задания и [добавьте его](./orders-fbs#tag/fbsLabelIdentifiers/paths/~1api~1v3~1orders~1%7BorderId%7D~1meta~1uin/put) заново - зарегистрирован в ГИИС ДМДК - указан корректно и считывается с бирки без ошибок - находится в обороте - `sgtin` - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `pending` — Проверка маркировки продолжается. Дождитесь изменения статуса проверки - `sgtinInvalidFormat` — Неверный формат маркировки - `sgtinNoGS` — Маркировка не содержит GS-разделитель `\u001d` - `sgtinHasInvalidSymbols` — Маркировка содержит некорректные символы или пробелы - `sgtinHasNonLatinSymbols` — Маркировка содержит символы, не относящиеся к специальным или латинице - `sgtinInvalidPattern` — Структура маркировки некорректна - `sgtinNotFound` — Маркировка не найдена в [Честном знаке](https://chestnyznak.ru) - `sgtinEmitted` — Маркировка эмитирована - `sgtinApplied` — Не пройдена процедура Ввод в оборот - `sgtinWrittenOff` — Списан - `sgtinRetired` — Выбыл - `sgtinWithdrawn` — Выбыл - `sgtinDisaggregation` — Расформирован - `sgtinDisaggregated` — Расформирован - `sgtinAppliedNotPaid` — Не оплачен - `gtin` - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `expiration` - `required` — Маркировка обязательна и не закреплена за сборочным заданием - `customsDeclaration` - `required` — Маркировка обязательна и не закреплена за сборочным заданием
      - `key` — string. Идентификатор маркировки
      - `value` — string. Значение идентификатора маркировки
- `message` — string. Описание ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
