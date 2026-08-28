---
title: Маркетинг и продвижение — все методы
api: wb-promotion
spec_version: promotion
operations: 39
source: "https://dev.wildberries.ru/docs/openapi/promotion"
content_sha: 37c56569e9fe0988
---

# Маркетинг и продвижение

Узнать больше о маркетинге и продвижении можно в справочном центре Методы маркетинга и продвижения позволяют: 1. Получать информацию о кампаниях [продвижения](./promotion#tag/campaigns) и [медиакампаниях](./promotion#tag/media) 2. [Создавать](./promotion#tag/creatingCampaigns) и [управлять](./promotion#tag/campaignManagement) кампаниями 3. Управлять [финансами](./promotion#tag/finances) кампаний 4. Выгружать [статистику](./promotion#tag/statistics) кампаний продвижения и медиакампаний 5. Работать с [календарём акций](./promotion#tag/promoCalendar) Данные синхронизируются с базой раз в 3 минуты. Статусы кампаний меняются раз в минуту. Ставки кампаний меняются раз в 30 секунд. Вы можете протестировать методы продвижения в [песочнице](/sandbox). Также в песочнице доступны [специальные методы](/docs/openapi-other/sandbox-environment#tag/Prodvizhenie) для управления тестовым балансом

Версия спеки: `promotion` · методов: **39**

Источник: https://dev.wildberries.ru/docs/openapi/promotion

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `DELETE` | `/adv/v0/normquery/bids` | searchClusters | [Удалить ставки поисковых кластеров{{ /adv/v0/normquery/bids }}](searchclusters/delete-adv-v0-normquery-bids.md) |
| `GET` | `/adv/v0/delete` | campaignManagement | [Удаление кампании{{ /adv/v0/delete }}](campaignmanagement/get-adv-v0-delete.md) |
| `GET` | `/adv/v0/pause` | campaignManagement | [Пауза кампании{{ /adv/v0/pause }}](campaignmanagement/get-adv-v0-pause.md) |
| `GET` | `/adv/v0/start` | campaignManagement | [Запуск кампании{{ /adv/v0/start }}](campaignmanagement/get-adv-v0-start.md) |
| `GET` | `/adv/v0/stop` | campaignManagement | [Завершение кампании{{ /adv/v0/stop }}](campaignmanagement/get-adv-v0-stop.md) |
| `GET` | `/adv/v1/advert` | media | [Информация о медиакампании{{ /adv/v1/advert }}](media/get-adv-v1-advert.md) |
| `GET` | `/adv/v1/adverts` | media | [Список медиакампаний{{ /adv/v1/adverts }}](media/get-adv-v1-adverts.md) |
| `GET` | `/adv/v1/balance` | finances | [Баланс{{ /adv/v1/balance }}](finances/get-adv-v1-balance.md) |
| `GET` | `/adv/v1/budget` | finances | [Бюджет кампании{{ /adv/v1/budget }}](finances/get-adv-v1-budget.md) |
| `GET` | `/adv/v1/count` | media | [Количество медиакампаний{{ /adv/v1/count }}](media/get-adv-v1-count.md) |
| `GET` | `/adv/v1/payments` | finances | [Получение истории пополнений счёта{{ /adv/v1/payments }}](finances/get-adv-v1-payments.md) |
| `GET` | `/adv/v1/promotion/count` | campaigns | [Списки кампаний{{ /adv/v1/promotion/count }}](campaigns/get-adv-v1-promotion-count.md) |
| `GET` | `/adv/v1/supplier/subjects` | creatingCampaigns | [Предметы для кампаний{{ /adv/v1/supplier/subjects }}](creatingcampaigns/get-adv-v1-supplier-subjects.md) |
| `GET` | `/adv/v1/upd` | finances | [Получение истории затрат{{ /adv/v1/upd }}](finances/get-adv-v1-upd.md) |
| `GET` | `/adv/v3/fullstats` | statistics | [Статистика кампаний{{ /adv/v3/fullstats }}](statistics/get-adv-v3-fullstats.md) |
| `GET` | `/api/advert/v0/bids/recommendations` | campaignManagement | [Рекомендуемые ставки для карточек товаров и поисковых кластеров{{ /api/advert/v0/bids/recommendations }}](campaignmanagement/get-api-advert-v0-bids-recommendations.md) |
| `GET` | `/api/advert/v1/config` | campaignManagement | [Конфигурационные значения продвижения{{ /api/advert/v1/config }}](campaignmanagement/get-api-advert-v1-config.md) |
| `GET` | `/api/advert/v2/adverts` | campaigns | [Информация о кампаниях{{ /api/advert/v2/adverts }}](campaigns/get-api-advert-v2-adverts.md) |
| `GET` | `/api/v1/calendar/promotions/details` | promoCalendar | [Детальная информация об акциях{{ /api/v1/calendar/promotions/details }}](promocalendar/get-api-v1-calendar-promotions-details.md) |
| `GET` | `/api/v1/calendar/promotions/nomenclatures` | promoCalendar | [Список товаров для участия в акции{{ /api/v1/calendar/promotions/nomenclatures }}](promocalendar/get-api-v1-calendar-promotions-nomenclatures.md) |
| `GET` | `/api/v1/calendar/promotions` | promoCalendar | [Список акций{{ /api/v1/calendar/promotions }}](promocalendar/get-api-v1-calendar-promotions.md) |
| `PATCH` | `/adv/v0/auction/nms` | campaignManagement | [Изменение списка карточек товаров в кампаниях{{ /adv/v0/auction/nms }}](campaignmanagement/patch-adv-v0-auction-nms.md) |
| `PATCH` | `/api/advert/v1/bids` | campaignManagement | [Изменение ставок в кампаниях{{ /api/advert/v1/bids }}](campaignmanagement/patch-api-advert-v1-bids.md) |
| `POST` | `/adv/v0/normquery/bids` | searchClusters | [Установить ставки для поисковых кластеров{{ /adv/v0/normquery/bids }}](searchclusters/post-adv-v0-normquery-bids.md) |
| `POST` | `/adv/v0/normquery/get-bids` | searchClusters | [Список ставок поисковых кластеров{{ /adv/v0/normquery/get-bids }}](searchclusters/post-adv-v0-normquery-get-bids.md) |
| `POST` | `/adv/v0/normquery/get-minus` | searchClusters | [Список минус-фраз кампаний{{ /adv/v0/normquery/get-minus }}](searchclusters/post-adv-v0-normquery-get-minus.md) |
| `POST` | `/adv/v0/normquery/list` | searchClusters | [Списки активных и неактивных поисковых кластеров{{ /adv/v0/normquery/list }}](searchclusters/post-adv-v0-normquery-list.md) |
| `POST` | `/adv/v0/normquery/set-minus` | searchClusters | [Установка и удаление минус-фраз{{ /adv/v0/normquery/set-minus }}](searchclusters/post-adv-v0-normquery-set-minus.md) |
| `POST` | `/adv/v0/normquery/stats` | statistics | [Статистика поисковых кластеров{{ /adv/v0/normquery/stats }}](statistics/post-adv-v0-normquery-stats.md) |
| `POST` | `/adv/v0/rename` | campaignManagement | [Переименование кампании{{ /adv/v0/rename }}](campaignmanagement/post-adv-v0-rename.md) |
| `POST` | `/adv/v1/budget/deposit` | finances | [Пополнение бюджета кампании{{ /adv/v1/budget/deposit }}](finances/post-adv-v1-budget-deposit.md) |
| `POST` | `/adv/v1/normquery/stats` | statistics | [Статистика по поисковым кластерам с детализацией по дням{{ /adv/v1/normquery/stats }}](statistics/post-adv-v1-normquery-stats.md) |
| `POST` | `/adv/v1/stats` | statistics | [Статистика медиакампаний{{ /adv/v1/stats }}](statistics/post-adv-v1-stats.md) |
| `POST` | `/adv/v2/seacat/save-ad` | creatingCampaigns | [Создать кампанию{{ /adv/v2/seacat/save-ad }}](creatingcampaigns/post-adv-v2-seacat-save-ad.md) |
| `POST` | `/adv/v2/supplier/nms` | creatingCampaigns | [Карточки товаров для кампаний{{ /adv/v2/supplier/nms }}](creatingcampaigns/post-adv-v2-supplier-nms.md) |
| `POST` | `/api/advert/v1/bids/min` | creatingCampaigns | [Минимальные ставки для карточек товаров{{ /api/advert/v1/bids/min }}](creatingcampaigns/post-api-advert-v1-bids-min.md) |
| `POST` | `/api/advert/v1/normquery/bids` | searchClusters | [Установить ставки для поисковых кластеров в валюте аккаунта продавца{{ /api/advert/v1/normquery/bids }}](searchclusters/post-api-advert-v1-normquery-bids.md) |
| `POST` | `/api/v1/calendar/promotions/upload` | promoCalendar | [Добавить товар в акцию{{ /api/v1/calendar/promotions/upload }}](promocalendar/post-api-v1-calendar-promotions-upload.md) |
| `PUT` | `/adv/v0/auction/placements` | campaignManagement | [Изменение мест размещения в кампаниях с ручной ставкой{{ /adv/v0/auction/placements }}](campaignmanagement/put-adv-v0-auction-placements.md) |
