---
title: Статусы заказов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/dbs-order-status-model.md"
fetched_at: "2026-09-24T02:13:20Z"
content_sha: ada4ac5950556fa1
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/dbs-order-status-model.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/dbs-order-status-model.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/dbs-order-status-model.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/concepts/dbs-order-status-model.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Как изменяются статусы заказов

Схема по изменению статусов показывает этапы, которые проходит DBS-заказ, и логику переходов между статусами. Это поможет соотнести статусы Маркета и вашей системы, корректно настроить интеграцию с Маркетом и не передавать лишние статусы и подстатусы.

**Обозначения:**

   * На схеме отражены статусы и подстатусы заказа на каждом этапе в формате `Статус Подстатус`. Например, `PROCESSING STARTED`.

      Список подстатусов `CANCELLED` смотрите в разделе [Подстатусы при отмене заказа](#cancelled-substatuses).

   * Стрелки показывают переходы между этапами, а их цвет — когда происходит этот переход:

      * зеленый — магазин изменил статус;
      * синий — Маркет изменил статус;
      * оранжевый — отмена заказа одной из сторон;
      * красный — исключительные случаи.

{% note warning "Передавайте статусы в том порядке, в котором они описаны на схеме" %}

Иначе это приведет к ошибке.

{% endnote %}

<!-- source: ru/_includes/mermaid/dbs-order-status-graph.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#FDF3E8',
      'tertiaryColor': '#FDF3E8',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

flowchart TB
    UserCreation(Покупатель создал заказ) --> Started[PROCESSING STARTED]
    Started[PROCESSING STARTED] -->|Заказ передан в доставку| Delivery[DELIVERY DELIVERY_SERVICE_RECEIVED]
    Started[PROCESSING STARTED] -->|Заказ отменен| Cancelled3[CANCELLED Подстатус]

    subgraph err1 [Обработка обращения]
        direction TB
        DeliveryUserNotReceived[DELIVERY DELIVERY_USER_NOT_RECEIVED] -->|Арбитр принимает решение об отмене| Cancelled1[CANCELLED Подстатус]
        DeliveryUserNotReceived[DELIVERY DELIVERY_USER_NOT_RECEIVED] -->|Заказ доставлен| Delivered2[DELIVERED DELIVERY_SERVICE_DELIVERED]
    end

    Delivery[DELIVERY DELIVERY_SERVICE_RECEIVED] -->|Срок доставки истек, покупатель не получил заказ| err1
    Delivery[DELIVERY DELIVERY_SERVICE_RECEIVED] --> |Заказ принят в ПВЗ| Pickup[PICKUP PICKUP_SERVICE_RECEIVED]
    Delivery[DELIVERY DELIVERY_SERVICE_RECEIVED] --> |Покупатель получил заказ| UserReceived[DELIVERY USER_RECEIVED]
    Delivery[DELIVERY DELIVERY_SERVICE_RECEIVED] --> |Заказ доставлен| Delivered[DELIVERED DELIVERY_SERVICE_DELIVERED]
    Delivery[DELIVERY DELIVERY_SERVICE_RECEIVED] --> |Заказ отменен| Cancelled4[CANCELLED Подстатус]

    Pickup[PICKUP PICKUP_SERVICE_RECEIVED] -->|Заказ доставлен| Delivered[DELIVERED DELIVERY_SERVICE_DELIVERED]
    Pickup[PICKUP PICKUP_SERVICE_RECEIVED] -->|Заказ отменен| Cancelled2[CANCELLED Подстатус]

    UserReceived[DELIVERY USER_RECEIVED] -->|Заказ доставлен| Delivered1[DELIVERED DELIVERY_SERVICE_DELIVERED]

    Delivered[DELIVERED DELIVERY_SERVICE_DELIVERED] --> |Срок доставки истек, покупатель не получил заказ| err2
    subgraph err2 [Обработка обращения]
        direction TB
        DeliveredUserNotReceived[DELIVERED DELIVERED_USER_NOT_RECEIVED] -->|Арбитр принимает решение об отмене| Cancelled[CANCELLED Подстатус]
    end

    linkStyle 0,7,12 stroke:dodgerblue,stroke-width:2px;
    linkStyle 2,9,11 stroke:orange,stroke-width:2px;
    linkStyle 3,5,13,14 stroke:tomato,stroke-width:2px;
    linkStyle 1,4,6,8,10 stroke:green,stroke-width:2px;

    style Delivered stroke:green,stroke-width:3px;
    style Delivered1 stroke:dodgerblue,stroke-width:3px;
    style Delivered2 stroke:green,stroke-width:3px;
    style DeliveredUserNotReceived stroke:green,stroke-width:3px;

    style Cancelled stroke:tomato,stroke-width:3px;
    style Cancelled1 stroke:tomato,stroke-width:3px;
    style Cancelled2 stroke:orange,stroke-width:3px;
    style Cancelled3 stroke:orange,stroke-width:3px;
    style Cancelled4 stroke:orange,stroke-width:3px;
```
<!-- endsource: ru/_includes/mermaid/dbs-order-status-graph.md -->


## Расшифровка схемы {#details}

#|
|| **Статус, подстатус и описание этапа** | **Кто меняет статус** | **Методы, с помощью которых меняется статус или приходит информация о заказе в этом статусе** ||

|| `PROCESSING`<br>
`STARTED`

Магазин обрабатывает заказ. | Маркет |

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)
||

|| `DELIVERY`<br>
`DELIVERY_SERVICE_RECEIVED`

Заказ передан в доставку. | Магазин |

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

|| `DELIVERY`<br>
`USER_RECEIVED`

Покупатель получил заказ.

Передается только при работе через Яндекс Доставку.| Маркет |

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) ||

|| `DELIVERY`<br>
`DELIVERY_USER_NOT_RECEIVED`

Срок доставки истек, покупатель не получил заказ.

Начинается арбитраж, по результатам которого заказ может быть отменен или переведен в статус `DELIVERED DELIVERY_SERVICE_DELIVERED`. | Маркет |

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) ||

|| `PICKUP`<br>
`PICKUP_SERVICE_RECEIVED`

Заказ принят в ПВЗ. | Магазин | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

|| `DELIVERED`<br>
`DELIVERY_SERVICE_DELIVERED`

Заказ доставлен.

Передается автоматически при работе через Яндекс Доставку.

Если вы доставляете самостоятельно, измените статус после вручения заказа.|
Маркет

Магазин |

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)||

|| `DELIVERED`<br>
`DELIVERED_USER_NOT_RECEIVED`

Срок доставки истек, покупатель не получил заказ.

Начинается арбитраж, по результатам которого заказ может быть отменен или остаться в том же статусе. | Маркет |

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) ||

|| `CANCELLED`<br>
[Подстатусы](#cancelled-substatuses)

Заказ отменен.

Чтобы отменить заказ, передайте подстатус `SHOP_FAILED`.

Если заказ находится в статусе `DELIVERY` или `PICKUP` и покупатель отменил его, [подтвердите отмену](*acceptOrderCancellation).
|
Маркет

Магазин

Покупатель|

[POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md)

[POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md)

[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||
|#

## Подстатусы при отмене заказа {#cancelled-substatuses}

### Подстатусы, которые может передавать магазин

В зависимости от текущего статуса заказа магазин может использовать следующие подстатусы отмены:

* **В статусе `PROCESSING`:**
  * `SHOP_FAILED` — магазин не может выполнить заказ.
  * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.
  * `USER_UNREACHABLE` — не удалось связаться с покупателем.
  * `INCORRECT_PERSONAL_DATA` — для заказа из-за рубежа указаны неправильные данные получателя, заказ не пройдет проверку на таможне.

* **В статусе `DELIVERY`:**
  * `SHOP_FAILED` — магазин не может выполнить заказ.
  * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.
  * `USER_UNREACHABLE` — не удалось связаться с покупателем.

* **В статусе `PICKUP`:**
  * `SHOP_FAILED` — магазин не может выполнить заказ.
  * `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.
  * `USER_UNREACHABLE` — не удалось связаться с покупателем.
  * `PICKUP_EXPIRED` — закончился срок хранения заказа в ПВЗ.

### Подстатусы, которые устанавливает покупатель или система

* `RESERVATION_EXPIRED` — покупатель не завершил оформление зарезервированного заказа в течение 10 минут.
* `USER_NOT_PAID` — покупатель не оплатил заказ (для типа оплаты `PREPAID`) в течение 30 минут.
* `USER_CHANGED_MIND` — покупатель отменил заказ по личным причинам.
* `USER_REFUSED_DELIVERY` — покупателя не устроили условия доставки.
* `USER_REFUSED_PRODUCT` — покупателю не подошел товар.
* `USER_REFUSED_QUALITY` — покупателя не устроило качество товара.
* `USER_IDENTIFICATION_MISMATCH` — идентификационный документ покупателя не совпадает с данными в заказе.
* `PURCHASE_GROUP_THRESHOLD_NOT_REACHED_CANCELLED` — заказ участвовал в групповой покупке и был отменен, потому что не было достигнуто нужное количество покупок.
* `REPLACING_ORDER` — покупатель решил заменить товар другим по собственной инициативе.
* `PROCESSING_EXPIRED` — значение более не используется.
* `PICKUP_EXPIRED` — закончился срок хранения заказа в ПВЗ.
* `TOO_MANY_DELIVERY_DATE_CHANGES` — заказ переносили слишком много раз.

Также могут возвращаться другие значения. Обрабатывать их не нужно.

[*acceptOrderCancellation]: [PUT v2/campaigns/{campaignId}/orders/{orderId}/cancellation/accept](../reference/orders/acceptOrderCancellation.md)
