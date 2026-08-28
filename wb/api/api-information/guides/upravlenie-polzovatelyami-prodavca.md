---
title: Управление пользователями продавца
api: wb-api-information
tag: sellerUserManagement
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/api-information"
content_sha: a5215a6124436457
---

# Управление пользователями продавца

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Пользователи

С помощью этих методов вы можете:
 - [Создать приглашение для пользователя](./api-information#tag/sellerUserManagement/operation/postV1Invite) с доступом к профилю продавца
 - [Получить список активных или приглашённых пользователей продавца](./api-information#tag/sellerUserManagement/operation/getV1Users)
 - [Изменить права доступа пользователей](./api-information#tag/sellerUserManagement/operation/putV1UsersAccess) к профилю продавца
 - [Закрыть доступ пользователю](./api-information#tag/sellerUserManagement/operation/deleteV1User) к профилю продавца

Управлять доступом пользователей можно только с токеном активного владельца профиля продавца.
