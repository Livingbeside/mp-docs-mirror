---
title: Доступы к методам по Api-Key
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/access.md"
fetched_at: "2026-08-28T11:51:09Z"
content_sha: 7dd8269bce375c27
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/access.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/access.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/access.md
  - href: ru/concepts/access.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Доступы к методам по Api-Key

Чтобы сотрудники могли выполнять только те методы, которые нужны им для работы, создайте токен с доступами к определенным группам методов.

[Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md#new-token)

## Какие бывают доступы {#method-groups}

Список доступов по переданному Api-Key-токену можно получить с помощью метода [POST v2/auth/token](https://yandex.ru/dev/market/partner-api/doc/ru/reference/auth/getAuthTokenInfo.md).

<!-- source: ru/_auto/scopes_summary/summary.md -->
#|
|| **Доступ** | **Название доступа в OpenAPI-спецификации** ||
|| [Полное управление кабинетом](*all-methods) | all-methods ||
|| [Просмотр всех данных](*all-methods_read-only) | all-methods:read-only ||
||
[Обработка заказов и учёт товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing.md)
|
inventory-and-order-processing
||
||
[Просмотр информации о заказах](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/inventory-and-order-processing_read-only.md)
|
inventory-and-order-processing:read-only
||
|| [Управление ценами](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing.md) | pricing ||
|| [Просмотр цен](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/pricing_read-only.md) | pricing:read-only ||
|| [Управление товарами и карточками](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management.md) | offers-and-cards-management ||
||
[Просмотр товаров и карточек](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/offers-and-cards-management_read-only.md)
|
offers-and-cards-management:read-only
||
|| [Продвижение товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion.md) | promotion ||
|| [Просмотр информации о продвижении товаров](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/promotion_read-only.md) | promotion:read-only ||
||
[Просмотр финансовой информации и отчётности](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/finance-and-accounting.md)
|
finance-and-accounting
||
|| [Общение с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/communication.md) | communication ||
|| [Настройка магазинов](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/settings-management.md) | settings-management ||
||
[Получение информации по FBY-заявкам](https://yandex.ru/dev/market/partner-api/doc/ru/_auto/scopes_summary/pages/supplies-management_read-only.md)
|
supplies-management:read-only
||
|#
<!-- endsource: ru/_auto/scopes_summary/summary.md -->


[*all-methods]: Все запросы к Маркету

[*all-methods_read-only]: Все запросы получения и просмотра данных
