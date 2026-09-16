---
title: Как пользоваться консолью
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/console.md"
fetched_at: "2026-09-16T02:26:46Z"
content_sha: ef985183842bfc7a
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/console.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/console.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/console.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/console.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Как пользоваться консолью

На странице описания каждого запроса есть две вкладки: **Info** и **Console**.

Консоль позволяет вам вручную составлять запросы и смотреть, что ответит Маркет.

{% note info "В консоли вы не можете передавать названия интеграций" %}

Поэтому у таких запросов на странице логов отображается тип интеграции **Консоль документации**, а не ее название.

[Подробнее о работе с логами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md)

{% endnote %}

## Как авторизоваться в консоли {#authorization}

1. Нажмите кнопку **Authorization**.
1. Выберите токен, который вы используете, — **apiKey** или **oauth2**.
1. Введите токен в формате:

    * `ACMA:I4c4CxCSYaI41RSC2uYWP2qj3Rhhm4knMiBEga5K:151c0664` — для Api-Key;

    * `Bearer y0_BfRRRRRV2L8sWWvNkSNNNNSrLHaNXg4cCMswFbL6MWab9lktL2KPsMw` — для OAuth.

Подробнее о получении и использовании токена:

*  [API-Key](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)
*  [OAuth 2.0](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md)

## Чтобы отправить запрос {#send-request}

{% note warning "Все запросы, отправляемые в консоль, и ее ответы — настоящие" %}

Если вы, например, попытаетесь отменить существующий заказ — он в самом деле отменится.

{% endnote %}

1. Откройте страницу с описанием нужного метода и перейдите на вкладку **Console**.
1. Заполните **Path params**, **Header params** и **Body**. Если вам понадобится описание параметра, вернитесь на вкладку **Info** и посмотрите его там — уже введенные данные не потеряются.
1. Нажмите **Send**.
