---
title: Получить информацию об опциях Конструктора тарифов
api: wb-api-information
method: GET
path: /api/common/v1/tariff-constructor/options
operation_id: getV1TariffConstructorOptions
tags:
  - sellerInformation
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: 556a29d71e02ab48
---

# Получить информацию об опциях Конструктора тарифов

`GET /api/common/v1/tariff-constructor/options`

Описание метода

 Информацию об опциях Конструктора тарифов можно получить с токеном любой [категории](./api-information#tag/authorization/Kategorii-tokenov)

 Метод [доступен](./api-information#tag/authorization/Pravila-ispolzovaniya-tokenov-dostupa-k-API) по
 Сервисному токену

Метод возвращает информацию обо всех опциях и пакетах опций, которые продавец подключил в [Конструкторе тарифов](https://seller.wildberries.ru/tariff-constructor).

Опции, входящие в подключённые пакеты, возвращаются в массиве `packages`. Опции, подключённые вне пакетов, возвращаются в массиве `options`.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 10 запросов |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `locale` | query | string (ru, en) | нет | Язык полей ответа: - `ru` — русский - `en` — английский |

## Ответы

**200** — Успешно

- `activeOptionCount` — number<int> **обязательный**. Количество активных опций, не включённых в пакеты
- `activePackageCount` — number<int> **обязательный**. Количество активных пакетов опций
- `totalCommissionRate` — number<float> **обязательный**. Итоговая комиссия за подключённые опции и пакеты, % от оборота
- `packages` — array[object] **обязательный**. Подключённые пакеты опций
  - `id` — string<uuid>. ID пакета
  - `slug` — string. Код пакета
  - `name` — string. Название пакета на языке из параметра `locale`
  - `status` — string (active, pendingActivation, pendingDeactivation). Статус пакета: - `active` — активен - `pendingActivation` — подключён, начнёт работать с 00:00 следующего дня - `pendingDeactivation` — отключён, перестанет работать с 00:00 следующего дня
  - `activatedAt` — string<date-time>. Дата активации пакета
  - `expiresAt` — string<date-time>. Дата окончания минимального срока действия пакета. До этого дня пакет опций нельзя отключить
  - `commissionRate` — number<float>. Комиссия за пакет, % от оборота
  - `periodDuration` — number<int>. Минимальный срок действия пакета в днях
  - `options` — array[object]. Опции, которые входят в пакет
    - `id` — string. ID опции
    - `slug` — string. Код опции
    - `name` — string. Название опции на языке из параметра `locale`
- `options` — array[object] **обязательный**. Подключённые опции
  - `id` — string. ID опции
  - `slug` — string. Код опции
  - `name` — string. Название опции на языке из параметра `locale`
  - `status` — string (active, pendingActivation, pendingDeactivation). Статус опции: - `active` — активна - `pendingActivation` — подключена, начнёт работать с 00:00 следующего дня - `pendingDeactivation` — отключена, перестанет работать с 00:00 следующего дня
  - `activatedAt` — string<date-time>. Дата активации опции
  - `expiresAt` — string<date-time>. Дата окончания минимального срока действия опции. До этого дня опцию нельзя отключить
  - `commissionRate` — number<float>. Стоимость подключения опции, % от оборота. Возвращается, если в ответе нет объекта `promotion`
  - `periodDuration` — number<int>. Минимальный срок действия опции в днях
  - `promotion` — object
    - `commissionRate` — number<float>. Стоимость подключения опции по акции, % от оборота
    - `expiresAt` — string<date-time>. Дата окончания действия цены по акции

**400** — Неправильный запрос

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `errors` — array[?]. Ошибки запроса с указанием параметров и деталей ошибок

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

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**404** — Не найдено

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `errors` — array[?]. Ошибки запроса с указанием параметров и деталей ошибок

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
