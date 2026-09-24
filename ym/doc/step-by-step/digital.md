---
title: Цифровые заказы
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md"
fetched_at: "2026-09-24T02:13:20Z"
content_sha: f517d4c6cc57280c
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/digital.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/digital.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Обработка заказов с цифровыми товарами

1. Получите список заказов — метод [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md).
   Если в заказе есть цифровые товары, в информации о доставке `delivery` в параметре `type` вернется значение `DIGITAL`.

1. Проверьте значение параметра `delivery.digitalGoods.type` — оно определяет, как передать товар покупателю:

   * **`EMAIL`** — код активации по почте.
     После перехода заказа в статус `PROCESSING` в течение 30 минут воспользуйтесь методом [POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md).
     Маркет отправит покупателю письмо с кодом и инструкцией на почту.

   * **`ACTIVATION_CODE`** — код активации в заказе на Маркете.
     После перехода заказа в статус `PROCESSING` в течение 30 минут воспользуйтесь методом [POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md).
     Покупатель получит инструкцию и код в чате с магазином, а в списке заказов сможет скопировать код.

   * **`STEAM_GIFT`** — игра подарком в Steam.
     В параметре `delivery.digitalGoods.steamLink` будет ссылка от покупателя на добавление в друзья на платформе Steam. Перейдите по ссылке, добавьте покупателя в друзья и отправьте ему игру.
     В течение трех часов передайте Маркету статус, что заказ доставлен — с помощью методов [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) или [POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md) или на странице заказа.

   * **`CHAT`** — игры и товары в чате с покупателем на Маркете.
     Передайте покупателю сертификат или способ получения цифрового товара в чате с магазином. После этого передайте Маркету статус, что заказ доставлен — с помощью методов [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) или [POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md) или на странице заказа.

{% note info "Если доставляете товары через чат с покупателем" %}

Для отправки сообщений через API используйте [чаты с покупателями](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/chats.md).

{% endnote %}

{% note warning "Не забудьте обновить статус заказа" %}

Для типов `STEAM_GIFT` и `CHAT` Маркет не переводит заказ в финальный статус автоматически. Передайте статус `DELIVERED` через API или на странице заказа.

{% endnote %}

{% note tip "Подключите API-уведомления" %}

Маркет отправит вам запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), когда появится новый заказ и изменится его статус.

[Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)

{% endnote %}
