---
title: Количество закреплённых и откреплённых отзывов{{ /api/feedbacks/v1/pins/count }}
api: wb-user-communication
method: GET
path: /api/feedbacks/v1/pins/count
operation_id: getFeedbacksV1PinsCount
tags:
  - pinnedFeedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/user-communication"
deprecated: false
content_sha: 5950294fec910273
---

# Количество закреплённых и откреплённых отзывов{{ /api/feedbacks/v1/pins/count }}

`GET /api/feedbacks/v1/pins/count`

Описание метода Метод возвращает количество закреплённых и откреплённых отзывов за заданный период. Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов | | Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов | | Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов | | Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

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

## Ответы

**200** — Успешно

- `data` — object **обязательный**
- `data` — integer. Количество отзывов

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
