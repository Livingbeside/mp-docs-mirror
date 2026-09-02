---
title: Медиафайлы
api: wb-item-management
tag: mediaFiles
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/item-management"
content_sha: 9fc5f976cbd09343
---

# Медиафайлы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Контент

 Узнать, как использовать методы в бизнес-кейсах, можно в [инструкции](/knowledge-base/articles/019d49a4-1320-71bb-9dac-8ba07e7177ce/rabota-s-tovarami) по работе с товарами

Управлять медиафайлами в карточке товара можно двумя способами:
 1. Через прямую [загрузку одного медиафайла](./work-with-products#tag/mediaFiles/paths/~1content~1v3~1media~1file/post) в карточку товара.
 2. Через [перечисление ссылок на медиафайлы](./work-with-products#tag/mediaFiles/paths/~1content~1v3~1media~1save/post). В этом случае новые медиафайлы заменяют медиафайлы, уже добавленные в карточку товара.
