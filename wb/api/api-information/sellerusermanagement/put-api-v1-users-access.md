---
title: Изменить права доступа пользователей{{ /api/v1/users/access }}
api: wb-api-information
method: PUT
path: /api/v1/users/access
operation_id: putV1UsersAccess
tags:
  - sellerUserManagement
spec_version: general
source: "https://dev.wildberries.ru/docs/openapi/api-information"
deprecated: false
content_sha: be1a2caeb310359a
---

# Изменить права доступа пользователей{{ /api/v1/users/access }}

`PUT /api/v1/users/access`

Описание метода Метод доступен по Персональному токену Метод меняет права доступа одному или нескольким пользователям. Обновляются только права доступа, переданные в параметрах запроса. Остальные поля остаются без изменений. Лимит запросов на один аккаунт продавца: | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 сек | 1 запрос | 1 сек | 5 запросов |

## Запрос

**Тело запроса** (`application/json`):

- `usersAccesses` — array[object] **обязательный**. Настройки доступа для пользователя
  - `userId` — integer. ID пользователя
  - `access` — array[object]. Настройки доступа к разделам профиля продавца
    - `code` — string (balance, brands, changeJam, discountPrice, finance, showcase, suppliersDocuments, supply, questions, pinFeedbacks, pointsForReviews, feedbacks…) **обязательный**. Код раздела профиля продавца, к которому пользователь получит доступ: * `balance` — Просмотр баланса и вывод средств * `brands` — Управление брендами * `changeJam` — Доступ к подключению подписки **Джем**: **А/Б тесты**, отметки на фото, автозапуски видео, сравнение карточек * `discountPrice` — Изменение цен на товары, управление скидками и акциями * `finance` — Финансовая аналитика. Статистика по балансу, финансовые отчёты, история платежей * `showcase` — Управление витриной магазина * `suppliersDocuments` — Просмотр и скачивание документов по работе с площадкой * `supply` — Создание и управление поставками FBW * `questions` — Просмотр и ответы на вопросы покупателей * `pinFeedbacks` — Возможность закреплять и откреплять отзывы * `pointsForReviews` — Баллы за отзывы * `feedbacks` — Просмотр и ответы на отзывы покупателей * `oldAnalyticsReports` — Отчёты * `marketplace` — Свой склад * `brandsFlow` — Мои бренды * `copyrightComplaints` — Обращения правообладателей * `pretrialClaims` — Досудебные претензии * `sellersChat` — Чат с покупателями * `brandzone` — Бренд-зона. Публикация изменений * `brandzoneSubscribe` — Управление подпиской бренд-зоны
    - `disabled` — boolean **обязательный**. * `true` — доступ к разделу запрещён * `false` — доступ к разделу разрешён

## Ответы

**200** — Успешно

**400** — Неправильный запрос

- `title` — string **обязательный**. Заголовок ошибки
- `detail` — string **обязательный**. Детали ошибки
- `requestId` — string **обязательный**. ID запроса
- `origin` — string **обязательный**. Название внутреннего сервиса
- `status` — number **обязательный**. HTTP статус-код

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

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
