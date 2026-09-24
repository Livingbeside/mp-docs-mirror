---
title: Экспресс-заказы
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/express.md"
fetched_at: "2026-09-24T02:13:19Z"
content_sha: ef82dce7061e6f4d
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/express.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/express.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/express.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/express.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Обработка Экспресс-заказов

API Маркета позволяет выполнять все те же действия, что выполняются в кабинете: смотреть новые заказы, получать для них ярлыки, что-то менять в них при необходимости и так далее.

{% note tip "Чтобы понимать, как все происходит" %}

Прочтите [статью о выполнении заказов](https://yandex.ru/support/marketplace/ru/orders/express/process).

{% endnote %}

## Шаг 1. Получение информации по заказам {#new-orders}

Читайте инструкцию: [Получение заказов](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/orders-receive.md)


## Шаг 2. Передача кодов маркировки {#marking-codes}

{% note info "Маркировка товаров в системе [«Честный ЗНАК»](https://честныйзнак.рф/) необязательна для заказов от физических лиц" %}

 

{% endnote %}

<!-- source: ru/_includes/mermaid/express-marking-code.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#94E1C4',
      'tertiaryColor': '#F84E57',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

sequenceDiagram
    participant Merchant as Ваш магазин
    participant Market as Яндекс Маркет

    rect rgb(251, 243, 232)
        note right of Merchant: Передача кодов маркировки, если они предусмотрены

        Merchant ->> Market: PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes
        Market -->> Merchant: OK
    end
    opt
        rect rgb(251, 243, 232)
            note right of Merchant: Необязательный шаг
            note right of Merchant: Получение статусов проверки кодов маркировки
            Merchant ->> Market: POST v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status
            Market -->> Merchant: OK: информация по проверке.
        end
    end

```
<!-- endsource: ru/_includes/mermaid/express-marking-code.md -->

Если для товара предусмотрена маркировка в «Честном знаке» или других системах маркировки, передайте Маркету код каждого проданного экземпляра.

Эти сведения передаются запросом [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md).

Если в заказе есть ювелирные изделия или товары с маркировкой в системе «Честный ЗНАК», после передачи кодов Маркет начнет их проверку. [Как получить статусы проверки](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md)


## Шаг 3. Печать ярлыков и передача статуса «Готов к отгрузке» {#label}

<!-- source: ru/_includes/mermaid/express-label.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#94E1C4',
      'tertiaryColor': '#F84E57',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

sequenceDiagram
    participant Merchant as Ваш магазин
    participant Market as Яндекс Маркет

    opt
      rect rgb(251, 243, 232)
        note right of Merchant: Необязательный шаг
        note right of Merchant: Передача внешнего идентификатора заказа
        Merchant ->> Market: POST v2/campaigns/{campaignId}/orders/{orderId}/external-id
        Market -->>+ Merchant: OK
      end
    end

    rect rgb(251, 243, 232)
      note right of Merchant: Получение ярлыков
      Merchant ->> Market: GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels
      Market -->> Merchant: OK: ярлыки.
    end

    rect rgb(251, 243, 232)
      Merchant ->> Merchant: Клеит ярлыки<br>на заказ.
      note right of Merchant: Передача статуса «Готов к отгрузке» ("status": "PROCESSING" "substatus": "READY_TO_SHIP")
      Merchant ->> Market: PUT v2/campaigns/{campaignId}/orders/{orderId}/status
      Market -->> Merchant: OK
    end
```
<!-- endsource: ru/_includes/mermaid/express-label.md -->

1. Упакуйте собранный заказ согласно правилам, подробно описанным в [Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/orders/express/packaging/rules).

1. Пока заказ находится в статусе `PROCESSING` с подстатусом `STARTED`, вы можете передать его внешний идентификатор — [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md).

1. Получите ярлыки с помощью запроса [GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md) и наклейте их на упакованный заказ.

1. Переведите заказ в статус **Готов к отгрузке** (`"status": "PROCESSING" "substatus": "READY_TO_SHIP"`) — запрос [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md).

## Шаг 4. Передача кода подтверждения и заказа курьеру {#verifyOrderEac}

<!-- source: ru/_includes/mermaid/express-verifyOrderEac.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#94E1C4',
      'tertiaryColor': '#F84E57',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

sequenceDiagram
    participant Merchant as Ваш магазин
    participant Market as Яндекс Маркет

    rect rgb(251, 243, 232)
        Merchant ->> Merchant: Получает код от курьера.
        note right of Merchant: Передача кода подтверждения
        Merchant ->> Market: PUT v2/campaigns/{campaignId}/orders/{orderId}/verifyEac
        Market -->>+ Merchant: OK
        Merchant ->>- Merchant: Отдает заказ курьеру.
    end
```
<!-- endsource: ru/_includes/mermaid/express-verifyOrderEac.md -->

1. Передайте код подтверждения, который вам назвал курьер, в запросе [PUT v2/campaigns/{campaignId}/orders/{orderId}/verifyEac](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/verifyOrderEac.md).

1. Если проверка кода выполнена успешно, передайте заказ курьеру.

## Если товара не хватает: отмена и сокращение заказа {#cancel-by-seller}

Если во время подготовки заказа вы обнаружили, что одного или нескольких товаров нет, отмените его целиком или частично. Это делается отдельными запросами.

<!-- source: ru/_includes/mermaid/express-cancel.md -->
```mermaid
%%{
  init: {
    'theme': 'base',
    'themeVariables': {
      'primaryColor': '#FDF3E8',
      'primaryTextColor': '#000000',
      'primaryBorderColor': '#BA9C80',
      'lineColor': '#BA9C80',
      'secondaryColor': '#94E1C4',
      'tertiaryColor': '#F84E57',
      'noteBkgColor': '#FED58D'
    }
  }
}%%

sequenceDiagram
    participant Merchant as Ваш магазин
    participant Market as Яндекс Маркет

    opt
      note right of Merchant: Необязательные шаги

      rect rgb(251, 243, 232)
        note right of Merchant: Если на складе не оказалось много нужных товаров, вы можете отменить заказ
        Merchant ->> Market: "status": "CANCELLED", "substatus": "SHOP_FAILED"<br>PUT v2/campaigns/{campaignId}/orders/{orderId}/status
        Market -->> Merchant: OK
      end

      rect rgb(251, 243, 232)
        note right of Merchant: Если на складе не хватает отдельных позиций, вы можете удалить их из заказа
        Merchant ->> Market: PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes
        Market -->> Merchant: OK
      end
    end
```
<!-- endsource: ru/_includes/mermaid/express-cancel.md -->

#|
||**Действие с заказом**| **Запрос**||
||Полная отмена заказа|[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md).

Переведите заказ в `"status":"CANCELLED"` `"substatus": "SHOP_FAILED"`.||
||Исключение товара из заказа|[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md)||
|#

{% note warning "Так нельзя делать часто" %}

Любое из этих действий понизит [индекс качества](*quality-index) магазина. Когда индекс качества снижается, магазин сталкивается с ограничениями.

{% endnote %}

[*quality-index]: Индекс качества — число от 0 до 100. Если магазин работает по модели FBY, индекс качества показывает, насколько хорошо продавец делает поставки на склады Маркета, а в моделях FBS, DBS и Экспресс индекс оценивает работу с заказами. [Узнать больше](https://yandex.ru/support/marketplace/quality/score/index.html)
