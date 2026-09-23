---
title: Маркетинг и продвижение — все методы
api: wb-promotion
spec_version: promotion
operations: 42
source: "https://dev.wildberries.ru/docs/openapi/promotion"
content_sha: b1eed32afce5e624
---

# Маркетинг и продвижение

Узнать больше о маркетинге и продвижении можно в [справочном центре](https://seller.wildberries.ru/instructions/category/59d92bd3-6ea0-40f2-b762-ca8835d7d42e?goBackOption=prevRoute&categoryId=479385c6-de01-4b4d-ad4e-ed941e65582e)

Методы маркетинга и продвижения позволяют:
 1. Получать информацию о кампаниях [продвижения](./promotion#tag/campaigns) и [медиакампаниях](./promotion#tag/media)
 2. [Создавать](./promotion#tag/creatingCampaigns) и [управлять](./promotion#tag/campaignManagement) кампаниями
 3. Управлять [финансами](./promotion#tag/finances) кампаний
 4. Выгружать [статистику](./promotion#tag/statistics) кампаний продвижения и медиакампаний
 5. Работать с [календарём акций](./promotion#tag/promoCalendar)

Данные синхронизируются с базой раз в 3 минуты. Статусы кампаний меняются раз в минуту. Ставки кампаний меняются раз в 30 секунд.

Вы можете протестировать методы продвижения в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/promotion) для управления тестовым балансом

Версия спеки: `promotion` · методов: **42** · разделов справки: **9**

Источник: https://dev.wildberries.ru/docs/openapi/promotion

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/adv/v0/normquery/bids` | searchClusters | [Удалить ставки поисковых кластеров](searchclusters/delete-adv-v0-normquery-bids.md) |
| `GET` | `/adv/v0/delete` | campaignManagement | [Удаление кампании](campaignmanagement/get-adv-v0-delete.md) |
| `GET` | `/adv/v0/pause` | campaignManagement | [Пауза кампании](campaignmanagement/get-adv-v0-pause.md) |
| `GET` | `/adv/v0/start` | campaignManagement | [Запуск кампании](campaignmanagement/get-adv-v0-start.md) |
| `GET` | `/adv/v0/stop` | campaignManagement | [Завершение кампании](campaignmanagement/get-adv-v0-stop.md) |
| `GET` | `/adv/v1/advert` | media | [Информация о медиакампании](media/get-adv-v1-advert.md) |
| `GET` | `/adv/v1/adverts` | media | [Список медиакампаний](media/get-adv-v1-adverts.md) |
| `GET` | `/adv/v1/balance` | finances | [Баланс](finances/get-adv-v1-balance.md) |
| `GET` | `/adv/v1/budget` | finances | [Бюджет кампании](finances/get-adv-v1-budget.md) |
| `GET` | `/adv/v1/count` | media | [Количество медиакампаний](media/get-adv-v1-count.md) |
| `GET` | `/adv/v1/payments` | finances | [Получение истории пополнений счёта](finances/get-adv-v1-payments.md) |
| `GET` | `/adv/v1/promotion/count` | campaigns | [Списки кампаний](campaigns/get-adv-v1-promotion-count.md) |
| `GET` | `/adv/v1/supplier/subjects` | creatingCampaigns | [Предметы для кампаний](creatingcampaigns/get-adv-v1-supplier-subjects.md) |
| `GET` | `/adv/v1/upd` | finances | [Получение истории затрат](finances/get-adv-v1-upd.md) |
| `GET` | `/adv/v3/fullstats` | statistics | [Статистика кампаний](statistics/get-adv-v3-fullstats.md) |
| `GET` | `/api/advert/v0/bids/recommendations` | campaignManagement | [Рекомендуемые ставки для карточек товаров и поисковых кластеров](campaignmanagement/get-api-advert-v0-bids-recommendations.md) |
| `GET` | `/api/advert/v0/daily-limits` | campaignManagement | [Получить настройки дневных лимитов кампаний](campaignmanagement/get-api-advert-v0-daily-limits.md) |
| `GET` | `/api/advert/v1/config` | campaignManagement | [Конфигурационные значения продвижения](campaignmanagement/get-api-advert-v1-config.md) |
| `GET` | `/api/advert/v2/adverts` | campaigns | [Информация о кампаниях](campaigns/get-api-advert-v2-adverts.md) |
| `GET` | `/api/v1/calendar/promotions/details` | promoCalendar | [Детальная информация об акциях](promocalendar/get-api-v1-calendar-promotions-details.md) |
| `GET` | `/api/v1/calendar/promotions/nomenclatures` | promoCalendar | [Список товаров для участия в акции](promocalendar/get-api-v1-calendar-promotions-nomenclatures.md) |
| `GET` | `/api/v1/calendar/promotions` | promoCalendar | [Список акций](promocalendar/get-api-v1-calendar-promotions.md) |
| `PATCH` | `/adv/v0/auction/nms` | campaignManagement | [Изменение списка карточек товаров в кампаниях](campaignmanagement/patch-adv-v0-auction-nms.md) |
| `PATCH` | `/api/advert/v1/bids` | campaignManagement | [Изменение ставок в кампаниях](campaignmanagement/patch-api-advert-v1-bids.md) |
| `POST` | `/adv/v0/normquery/bids` | searchClusters | [Установить ставки для поисковых кластеров](searchclusters/post-adv-v0-normquery-bids.md) |
| `POST` | `/adv/v0/normquery/get-bids` | searchClusters | [Список ставок поисковых кластеров](searchclusters/post-adv-v0-normquery-get-bids.md) |
| `POST` | `/adv/v0/normquery/get-minus` | searchClusters | [Список минус-фраз кампаний](searchclusters/post-adv-v0-normquery-get-minus.md) |
| `POST` | `/adv/v0/normquery/list` | searchClusters | [Списки активных и неактивных поисковых кластеров](searchclusters/post-adv-v0-normquery-list.md) |
| `POST` | `/adv/v0/normquery/set-minus` | searchClusters | [Установка и удаление минус-фраз](searchclusters/post-adv-v0-normquery-set-minus.md) |
| `POST` | `/adv/v0/normquery/stats` | statistics | [Статистика поисковых кластеров](statistics/post-adv-v0-normquery-stats.md) |
| `POST` | `/adv/v0/rename` | campaignManagement | [Переименование кампании](campaignmanagement/post-adv-v0-rename.md) |
| `POST` | `/adv/v1/budget/deposit` | finances | [Пополнение бюджета кампании](finances/post-adv-v1-budget-deposit.md) |
| `POST` | `/adv/v1/normquery/stats` | statistics | [Статистика по поисковым кластерам с детализацией по дням](statistics/post-adv-v1-normquery-stats.md) |
| `POST` | `/adv/v1/stats` | statistics | [Статистика медиакампаний](statistics/post-adv-v1-stats.md) |
| `POST` | `/adv/v2/seacat/save-ad` | creatingCampaigns | [Создать кампанию](creatingcampaigns/post-adv-v2-seacat-save-ad.md) |
| `POST` | `/adv/v2/supplier/nms` | creatingCampaigns | [Карточки товаров для кампаний](creatingcampaigns/post-adv-v2-supplier-nms.md) |
| `POST` | `/api/advert/v1/bids/min` | creatingCampaigns | [Минимальные ставки для карточек товаров](creatingcampaigns/post-api-advert-v1-bids-min.md) |
| `POST` | `/api/advert/v1/normquery/bids` | searchClusters | [Установить ставки для поисковых кластеров в валюте аккаунта продавца](searchclusters/post-api-advert-v1-normquery-bids.md) |
| `POST` | `/api/advert/v2/budget` | finances | [Остатки бюджетов кампаний](finances/post-api-advert-v2-budget.md) |
| `POST` | `/api/v1/calendar/promotions/upload` | promoCalendar | [Добавить товар в акцию](promocalendar/post-api-v1-calendar-promotions-upload.md) |
| `PUT` | `/adv/v0/auction/placements` | campaignManagement | [Изменение мест размещения в кампаниях с ручной ставкой](campaignmanagement/put-adv-v0-auction-placements.md) |
| `PUT` | `/api/advert/v0/daily-limits` | campaignManagement | [Настройка дневных лимитов кампаний](campaignmanagement/put-api-advert-v0-daily-limits.md) |
