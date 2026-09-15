---
title: Медиафайлы
api: wb-item-management
tag: mediaFiles
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: c7a3d1c78f8449fd
---

# Медиафайлы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

Управлять медиафайлами в карточке товара можно двумя способами:
 1. Через прямую [загрузку одного медиафайла](./item-management#tag/mediaFiles/operation/postV3MediaFile) в карточку товара.
 2. Через [перечисление ссылок на медиафайлы](./item-management#tag/mediaFiles/operation/postV3MediaSave). В этом случае новые медиафайлы заменяют медиафайлы, уже добавленные в карточку товара.
