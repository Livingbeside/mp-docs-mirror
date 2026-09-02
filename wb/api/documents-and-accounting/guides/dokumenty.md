---
title: Документы
api: wb-documents-and-accounting
tag: documents
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/documents-and-accounting"
content_sha: c01301605da604fd
---

# Документы

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Документы

С помощью этих методов вы можете получить [документы продавца](https://seller.wildberries.ru/supplementary-agreements) различных категорий: акты, бухгалтерские отчёты, оферты, письма, списки товаров, УКД, УПД, уведомления и так далее.

Для работы с документами получите списки:
1. [Категорий документов](./financial-reports-and-accounting#tag/documents/operation/getV1DocumentsCategories)
2. [Документов продавца](./financial-reports-and-accounting#tag/documents/operation/getV1DocumentsList), доступных для загрузки

Вы можете загрузить [один](./financial-reports-and-accounting#tag/documents/operation/getV1DocumentsDownload) или [несколько](./financial-reports-and-accounting#tag/documents/operation/postV1DocumentsDownloadAll) документов из полученного списка.
