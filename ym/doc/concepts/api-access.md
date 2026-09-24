---
title: Управление доступом к API
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md"
fetched_at: "2026-09-24T02:13:12Z"
content_sha: 8b889e8121cd45b3
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/api-access.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/api-access.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Управление доступом к API

Если API Яндекс Маркета недоступно, выполните следующие шаги: проверьте статус доступа, определите причину блокировки и устраните её.

{% note info "Логи запросов" %}

При недоступном API запросы не выполняются и не записываются в [логи запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md).

{% endnote %}

## Как узнать статус доступа к API {#check-status}

Используйте методы:

* [GET v2/campaigns/{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md) — для конкретного магазина;
* [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md) — для всех магазинов кабинета.

В ответе проверьте параметр `apiAvailability`:

* `AVAILABLE` — API доступно.
* [`DISABLED_BY_INACTIVITY`](#inactivity) — API отключено из-за неактивности.
* [`DISABLED_BY_NO_ACTIVE_CONTRACT`](#no-contract) — API отключено из-за отсутствия активного договора.
* [`MANUALLY_DISABLED`](#manually-disabled) — интеграция выключена вручную.
* [`DISABLED_BY_NO_PLACEMENT_TYPE`](#no-placement-program) — магазин не подключен к программе размещения.

Также статус доступа к API можно посмотреть в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any/api-settings) в разделе **Настройки** → **API и модули**.

{% note warning %}

При отключении магазина от API блокируются запросы от всех интеграций к этому магазину.

{% endnote %}

## Причины блокировки и способы решения {#reasons}

### Интеграция выключена вручную {#manually-disabled}

**Статус:** `MANUALLY_DISABLED`

**Сообщение об ошибке:**

```text translate=no
API for campaign {campaignId} manually disabled.
```

**Как восстановить доступ:**

Включите интеграцию в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any/api-settings).

### Магазин неактивен более 90 дней {#inactivity}

**Статус:** `DISABLED_BY_INACTIVITY`

**Сообщение об ошибке:**

```text translate=no
API for campaign {campaignId} disabled due to inactivity.
```

**Причина:** Магазин не размещал товары на витрине больше 90 дней.

**Как восстановить доступ:**

1. Включите интеграцию в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any/api-settings).
2. Проверьте, что интеграция работает корректно в [логах запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md).
3. Проверьте, что цены и остатки товаров актуальны.
4. Отправьте магазин на модерацию, чтобы вернуться на витрину.

### Нет активного договора {#no-contract}

**Статус:** `DISABLED_BY_NO_ACTIVE_CONTRACT`

**Сообщение об ошибке:**

```text translate=no
API for campaign {campaignId} disabled because there are no active contracts with Market.
```

**Как восстановить доступ:**

Завершите подключение кабинета в разделе [«Юридические данные»](https://partner.market.yandex.ru/business/any).

### Магазин не подключен к программе размещения {#no-placement-program}

**Статус:** `DISABLED_BY_NO_PLACEMENT_TYPE`

**Сообщение об ошибке:**

```text translate=no
API for campaign {campaignId} disabled because it has no placement program.
```

**Как восстановить доступ:**

Подключите магазин к программе размещения в [кабинете продавца на Маркете](https://partner.market.yandex.ru).

### Все магазины кабинета отключены {#business-disabled}

**Сообщение об ошибке:**

```text translate=no
API for business {businessId} disabled because it has only disabled partners.
```

**Причина:** Все магазины в кабинете отключены.

**Как восстановить доступ:**

Включите API хотя бы для одного магазина кабинета в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any/api-settings).

## Проверка доступа после восстановления {#verify-access}

После выполнения действий по восстановлению доступа:

1. Подождите до минуты — изменения могут применяться не мгновенно.
2. Проверьте статус доступа методом [GET v2/campaigns/{campaignId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaign.md) или [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md).
3. Убедитесь, что параметр `apiAvailability` имеет значение `AVAILABLE`.
4. Выполните тестовый запрос к API.
