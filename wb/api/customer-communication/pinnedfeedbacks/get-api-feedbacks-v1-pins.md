---
title: Список закреплённых и откреплённых отзывов
api: wb-customer-communication
method: GET
path: /api/feedbacks/v1/pins
operation_id: getFeedbacksV1Pins
tags:
  - pinnedFeedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: 1fb5c4c6d6334349
---

# Список закреплённых и откреплённых отзывов

`GET /api/feedbacks/v1/pins`

Описание метода

Метод предоставляет список закреплённых и откреплённых отзывов.

Откреплёнными считаются только отзывы, которые были откреплены автоматически по причинам, указанным в ответе в поле `unpinnedCause`.

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
| `state` | query | string (pinned, unpinned) | нет | Закреплён ли отзыв: - `pinned` — да - `unpinned` — нет |
| `pinOn` | query | string (nm, imt) | нет | Место закрепления отзыва: - `nm` — карточка товара - `imt` — группа [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров |
| `imtId` | query | integer | нет | ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров. Един для всех артикулов WB группы объединённых карточек. У каждой карточки товара есть `imtId`, даже если она не объединена с другими карточками |
| `nmId` | query | integer | нет | Артикул WB |
| `feedbackId` | query | integer | нет | ID отзыва |
| `dateFrom` | query | string<date-time> | нет | Дата закрепления первого отзыва в списке |
| `dateTo` | query | string<date-time> | нет | Дата закрепления последнего отзыва в списке |
| `next` | query | integer | нет | ID последней операции закрепления (пагинатор) |
| `limit` | query | integer | нет | Количество отзывов на одной странице (пагинация) |

## Ответы

**200** — Успешно

- `data` — object **обязательный**
- `data` — array[object]
  - `changeStateAt` — string<date-time> **обязательный**. Дата и время закрепления или открепления
  - `imtId` — integer **обязательный**. ID для [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
  - `nmId` — integer **обязательный**. Артикул WB
  - `pinId` — integer **обязательный**. ID операции закрепления отзыва
  - `pinMethod` — string (subscription, tariff) **обязательный**. Метод закрепления: - `subscription` — подписка Джем - `tariff` — тарифная опция
  - `pinOn` — string (imt, nm) **обязательный**. Место закрепления отзыва: - `nm` — карточка товара - `imt` — группа [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
  - `feedbackId` — string **обязательный**. ID отзыва
  - `state` — string (pinned, unpinned) **обязательный**. Закреплён ли отзыв: - `pinned` — да - `unpinned` — нет
  - `unpinnedCause` — string (sysTariffUnpinned, sysLimitReached, sysNoratingUnpinned, sysAdditionalSlot). Причина открепления отзыва: - `sysTariffUnpinned` — закончилась подписка или тарифная опция - `sysLimitReached` — закончился общий лимит по подписке - `sysNoratingUnpinned` — отзыв исключён из рейтинга. Например, удалён или забанен - `sysAdditionalSlot` — к карточке или к группе [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек прикреплено максимальное количество отзывов
- `next` — integer. Параметр пагинации. Укажите это значение в запросе, чтобы получить следующий пакет данных. Если поле отсутствует, вы получили все данные

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
