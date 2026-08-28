---
title: Общее — все методы
api: wb-api-information
spec_version: general
operations: 10
source: "https://dev.wildberries.ru/docs/openapi/api-information"
content_sha: 82edd10b922a3a1b
---

# Общее

В этом разделе: - [общая информация о WB API](./api-information#tag/introduction) - как [начать работу с WB API](./api-information#tag/introduction/Kak-nachat-rabotu-s-API) - как [авторизоваться](./api-information#tag/authorization) и [создавать токены](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) - основные [статус-коды ответов](./api-information#tag/introduction/Status-kody-HTTP) - [лимиты запросов](./api-information#tag/introduction/Limity-zaprosov) - как обратиться в [поддержку](./api-information#tag/introduction/Podderzhka) С помощью методов этого раздела вы можете: - проверить [подключение к WB API](./api-information#tag/connectionCheck/operation/getPing) - получить [новости портала продавцов](./api-information#tag/newsApi/operation/getV2News) - получить [информацию о продавце](./api-information#tag/sellerInformation/operation/getV1SellerInfo) - [управлять пользователями продавца](./api-information#tag/sellerUserManagement)

Версия спеки: `general` · методов: **10**

Источник: https://dev.wildberries.ru/docs/openapi/api-information

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/api/v1/user` | sellerUserManagement | [Удалить пользователя{{ /api/v1/user }}](sellerusermanagement/delete-api-v1-user.md) |
| `GET` | `/api/common/v1/rating` | sellerInformation | [Получить рейтинг продавца{{ /api/common/v1/rating }}](sellerinformation/get-api-common-v1-rating.md) |
| `GET` | `/api/common/v1/subscriptions` | sellerInformation | [Получить информацию о подписке Джем{{ /api/common/v1/subscriptions }}](sellerinformation/get-api-common-v1-subscriptions.md) |
| `GET` | `/api/common/v1/tariff-constructor/options` | sellerInformation | [Получить информацию об опциях Конструктора тарифов{{ /api/common/v1/tariff-constructor/options }}](sellerinformation/get-api-common-v1-tariff-constructor-options.md) |
| `GET` | `/api/communications/v2/news` | newsApi | [Получение новостей портала продавцов{{ /api/communications/v2/news }}](newsapi/get-api-communications-v2-news.md) |
| `GET` | `/api/v1/seller-info` | sellerInformation | [Получить информацию о продавце{{ /api/v1/seller-info }}](sellerinformation/get-api-v1-seller-info.md) |
| `GET` | `/api/v1/users` | sellerUserManagement | [Получить список активных или приглашённых пользователей продавца{{ /api/v1/users }}](sellerusermanagement/get-api-v1-users.md) |
| `GET` | `/ping` | connectionCheck | [Проверка подключения{{ /ping }}](connectioncheck/get-ping.md) |
| `POST` | `/api/v1/invite` | sellerUserManagement | [Создать приглашение для нового пользователя{{ /api/v1/invite }}](sellerusermanagement/post-api-v1-invite.md) |
| `PUT` | `/api/v1/users/access` | sellerUserManagement | [Изменить права доступа пользователей{{ /api/v1/users/access }}](sellerusermanagement/put-api-v1-users-access.md) |
