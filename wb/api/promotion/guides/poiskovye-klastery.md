---
title: Поисковые кластеры
api: wb-promotion
tag: searchClusters
group: ""
kind: guide
source: "https://dev.wildberries.ru/docs/openapi/promotion"
content_sha: fcc46aeeaae6571b
---

# Поисковые кластеры

Для доступа к методам используйте [токен](./api-information#tag/authorization/Kak-sozdat-personalnyj-bazovyj-ili-testovyj-token) для категории Продвижение

**Поисковые кластеры**

**Кластер запросов** — это сгруппированный список запросов, по которым покупатели ищут товары на WB. В кластер входят:
 - синонимы
 - запросы в разном роде: мужской, женский, средний
 - запросы с опечатками
 - разные формы слова
 - близкие по смыслу словосочетания

Например, в кластер `футболка мужская` войдут также запросы `футболка мужкая`, `футболки мужские с рукавом`, `футболки мужские` и другие похожие словосочетания.

Чтобы получить кластеры, по которым уже были показы, используйте метод [статистики поисковых запросов](./promotion#tag/statistics/operation/postV0NormqueryStats).

Для кампаний с ручной ставкой можно [установить](./promotion#tag/searchClusters/operation/postV1NormqueryBids) или [удалить](./promotion#tag/searchClusters/operation/deleteV0NormqueryBids) ставки в валюте [аккаунта продавца](https://cmp.wildberries.ru/campaigns/finances). Валюту аккаунта продавца и шаги ставок можно уточнить в ответе метода [GET /api/advert/v1/config](./promotion#tag/campaignManagement/operation/getV1Config). Ставки индивидуальны для каждого поискового кластера.

**Исключения**

[Установите минус-фразы](./promotion#tag/searchClusters/operation/postV0NormquerySetMinus), чтобы исключить кластеры запросов из кампаний. Товар не будет продвигаться по минус-фразам.
