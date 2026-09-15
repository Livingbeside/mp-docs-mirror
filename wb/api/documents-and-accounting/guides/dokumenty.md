---
title: Документы
api: wb-documents-and-accounting
tag: documents
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/documents-and-accounting"
content_sha: 3633f8b0aad0919c
---

# Документы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Документы

С помощью этих методов вы можете получить [документы продавца](https://seller.wildberries.ru/supplementary-agreements) различных категорий: акты, бухгалтерские отчёты, оферты, письма, списки товаров, УКД, УПД, уведомления и так далее.

Для работы с документами получите списки:
1. [Категорий документов](./documents-and-accounting#tag/documents/operation/getV1DocumentsCategories)
2. [Документов продавца](./documents-and-accounting#tag/documents/operation/getV1DocumentsList), доступных для загрузки

Вы можете загрузить [один](./documents-and-accounting#tag/documents/operation/getV1DocumentsDownload) или [несколько](./documents-and-accounting#tag/documents/operation/postV1DocumentsDownloadAll) документов из полученного списка.
