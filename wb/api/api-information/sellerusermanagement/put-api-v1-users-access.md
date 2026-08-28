---
title: Изменить права доступа пользователей
api: wb-api-information
method: PUT
path: /api/v1/users/access
operation_id: putV1UsersAccess
tags:
  - sellerUserManagement
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: 722751a3b952ec19
---

# Изменить права доступа пользователей

`PUT /api/v1/users/access`

Описание метода

 Метод доступен по
 Персональному токену

Метод меняет права доступа одному или нескольким пользователям.

Обновляются только права доступа, переданные в параметрах запроса. Остальные поля остаются без изменений.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 сек | 1 запрос | 1 сек | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `usersAccesses` — array[object] **обязательный**. Настройки доступа для пользователя
  - `access` — array[object]. Настройки доступа к разделам профиля продавца
    - `code` — string (balance, brands, changeJam, discountPrice, finance, showcase, suppliersDocuments, supply, questions, pinFeedbacks, pointsForReviews, feedbacks…) **обязательный**. Код раздела профиля продавца, к которому пользователь получит доступ: * `balance` — Просмотр баланса и вывод средств * `brands` — Управление брендами * `changeJam` — Доступ к подключению подписки **Джем**: **А/Б тесты**, отметки на фото, автозапуски видео, сравнение карточек * `discountPrice` — Изменение цен на товары, управление скидками и акциями * `finance` — Финансовая аналитика. Статистика по балансу, финансовые отчёты, история платежей * `showcase` — Управление витриной магазина * `suppliersDocuments` — Просмотр и скачивание документов по работе с площадкой * `supply` — Создание и управление поставками FBW * `questions` — Просмотр и ответы на вопросы покупателей * `pinFeedbacks` — Возможность закреплять и откреплять отзывы * `pointsForReviews` — Баллы за отзывы * `feedbacks` — Просмотр и ответы на отзывы покупателей * `oldAnalyticsReports` — Отчёты * `marketplace` — Свой склад * `brandsFlow` — Мои бренды * `copyrightComplaints` — Обращения правообладателей * `pretrialClaims` — Досудебные претензии * `sellersChat` — Чат с покупателями * `brandzone` — Бренд-зона. Публикация изменений * `brandzoneSubscribe` — Управление подпиской бренд-зоны
    - `disabled` — boolean **обязательный**. * `true` — доступ к разделу запрещён * `false` — доступ к разделу разрешён
  - `userId` — integer. ID пользователя

## Ответы

**200** — Успешно

**400** — Неправильный запрос

- `detail` — string **обязательный**. Детали ошибки
- `origin` — string **обязательный**. Название внутреннего сервиса
- `requestId` — string **обязательный**. ID запроса
- `status` — number **обязательный**. HTTP статус-код
- `title` — string **обязательный**. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
