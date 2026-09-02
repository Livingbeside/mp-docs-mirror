---
title: Закрепить отзывы
api: wb-customer-communication
method: POST
path: /api/feedbacks/v1/pins
operation_id: postFeedbacksV1Pins
tags:
  - pinnedFeedbacks
spec_version: communication
source: "https://dev.wildberries.ru/docs/openapi/customer-communication"
deprecated: false
content_sha: f1a19c79ce444cd7
---

# Закрепить отзывы

`POST /api/feedbacks/v1/pins`

Описание метода

Метод позволяет закрепить отзывы в карточке товара или в группе [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек. 

Чтобы получить ID отзывов, используйте метод [Список закреплённых и откреплённых отзывов](./user-communication#tag/pinnedFeedbacks/operation/getFeedbacksV1Pins).

Метод доступен по [подписке Джем](https://seller.wildberries.ru/monetization/jam) или c [тарифной опцией](https://seller.wildberries.ru/tariff-constructor) **Закрепление отзыва**.

Лимит запросов на один аккаунт продавца для всех методов категории Вопросы и отзывы:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Сервисный | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый с секретом | 1 сек | 3 запроса | 333 мс | 6 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Запрос

**Тело запроса** (`application/json`):

- `pinMethod` — string (tariff, subscription) **обязательный**. Метод закрепления: - `subscription` — подписка Джем - `tariff` — тарифная опция
- `pinOn` — string (nm, imt) **обязательный**. Место закрепления отзыва: - `nm` — карточка товара - `imt` — группа [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
- `feedbackId` — string **обязательный**. ID отзыва

## Ответы

**200** — Успешно

- `data` — object **обязательный**
- `data` — array[object]
  - `feedbackId` — string **обязательный**. ID отзыва
  - `pinId` — integer. ID операции закрепления. Если поле отсутствует — закрепить отзыв не удалось
  - `pinMethod` — string (tariff, subscription) **обязательный**. Метод закрепления: - `subscription` — подписка Джем - `tariff` — тарифная опция
  - `pinOn` — string (nm, imt) **обязательный**. Место закрепления отзыва: - `nm` — карточка товара - `imt` — группа [объединённых](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami#obuedinenie-i-razuedinenie-kartochek-tovarov) карточек товаров
  - `isErrors` — boolean **обязательный**. Есть ли ошибки
  - `errors` — array[object]. Детали ошибок
    - `origin` — string **обязательный**. ID внутреннего сервиса WB
    - `detail` — string. Детали ошибки
    - `requestId` — string **обязательный**. ID запроса
    - `status` — string (feedbackNotFound, itemNotFound, feedbackMismatch, itemNoImages, feedbackExcluded, imtNotDisplayed, globalLimitReached, unitLimitReached, tariffRestriction, subscriptionRestriction, alreadyPinned, bodyNotValid) **обязательный**. Статус
    - `title` — string **обязательный**. Заголовок ошибки

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

**403** — Доступ запрещён

- `detail` — string. Детали ошибки
- `origin` — string **обязательный**. ID внутреннего сервиса WB
- `requestId` — string **обязательный**. ID запроса
- `status` — integer **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
