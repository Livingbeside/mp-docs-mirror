---
title: Изменение цен
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-change-prices.md"
fetched_at: "2026-09-04T01:57:48Z"
content_sha: 78ced4b1b0d018ad
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/assortment-change-prices.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/assortment-change-prices.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/assortment-change-prices.md
  - href: ru/step-by-step/assortment-change-prices.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Как изменить цены на товары

Вы можете изменить цену, которая действует во всех магазинах, или цену для отдельного магазина.

Вам доступен метод [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md), если в кабинете продавца на Маркете есть возможность установить уникальные цены в отдельных магазинах. Как это проверить — в методе [POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md) в параметре `onlyDefaultPrice` возвращается значение `false`.

В ином случае используйте метод управления ценами, которые действуют во всех магазинах, — [POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md).

{% note tip "Слишком резкое изменение цены приведет к тому, что товар попадет в **карантин**" %}

Карантин нужен, чтобы товар не оказался на витрине с неправильной ценой из-за технической ошибки.

Порог срабатывания карантина можно настроить в кабинете. О том, как это сделать, читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/assortment/operations/prices.html#quarantine).

{% endnote %}

{% list tabs %}

- Цена для всех магазинов

    <!-- source: ru/_includes/mermaid/assortment-business-price.md -->
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
            note right of Merchant: Расчет стоимости услуг Маркета
            Merchant ->> Market: Параметры товаров<br>POST v2/tariffs/calculate
            Market -->> Merchant: OK: стоимость услуг для товаров с заданными параметрами.
        end

        rect rgb(251, 243, 232)
            note right of Merchant: Передача новых цен
            Merchant ->>+ Market: Изменившиеся цены<br>POST v2/businesses/{businessId}/offer-prices/updates
            Market ->> Market: Проверяет и либо применяет цены,<br>либо отправляет товар в карантин.
            Market -->>- Merchant: OK
        end

        opt
          rect rgb(251, 243, 232)
              note right of Merchant: Необязательный шаг
              note right of Merchant: Передача НДС
              Merchant ->>+ Market: НДС в параметре vat<br>POST v2/campaigns/{campaignId}/offers/update
              Market ->> Market: Применяет<br>переданный НДС.
              Market -->>- Merchant: OK
          end
        end

        rect rgb(251, 243, 232)
            note right of Merchant: Проверка, не попал ли какой товар в карантин
            Merchant ->> Market: POST v2/businesses/{businessId}/price-quarantine
            Market -->> Merchant: OK: список товаров в карантине.
            alt Карантин не пустой, и в ценах есть ошибки
                Merchant ->>+ Market: Исправленные цены<br>POST v2/businesses/{businessId}/offer-prices/updates
                Market ->> Market: Проверяет<br>и устанавливает цены.
                Market -->>- Merchant: OK
            else Карантин не пустой, но все цены правильные
                Merchant ->>+ Market: POST v2/businesses/{businessId}/price-quarantine/confirm
                Market ->> Market: Убирает товары<br>из карантина.
                Market -->>- Merchant: OK
            end
        end
    ```
    <!-- endsource: ru/_includes/mermaid/assortment-business-price.md -->

    1. Чтобы узнать стоимость услуг Маркета для конкретных товаров, передайте их параметры в запросе [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md).
    1. Передайте новые цены для всех магазинов с помощью запроса [POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md).

        [Как получить установленные цены](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getDefaultPrices.md)
    1. При необходимости передайте НДС — параметр `vat` в запросе [POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md).
    1. Убедитесь, что ни один из товаров не попал в карантин с помощью запроса [POST v2/businesses/{businessId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getBusinessQuarantineOffers.md).
    1. Если карантин не пустой, проверьте цены на товары. Ошибочно установленные цены для всех магазинов можно исправить запросом [POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md).
    1. После того как в карантине останутся только правильные цены, подтвердите их запросом [POST v2/businesses/{businessId}/price-quarantine/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmBusinessPrices.md). Если ложные срабатывания карантина случаются часто, подумайте о том, чтобы изменить его порог по [инструкции](https://yandex.ru/support/marketplace/assortment/operations/prices.html#quarantine).

- Цена для отдельного магазина

    <!-- source: ru/_includes/mermaid/assortment-price.md -->
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
            note right of Merchant: Расчет стоимости услуг Маркета
            Merchant ->>+ Market: Параметры товаров<br>POST v2/tariffs/calculate
            Market -->> Merchant: OK: стоимость услуг для товаров с заданными параметрами.
          end

          rect rgb(251, 243, 232)
              note right of Merchant: Передача новых цен
              Merchant ->>+ Market: Изменившиеся цены<br>POST v2/campaigns/{campaignId}/offer-prices/updates
              Market ->> Market: Проверяет и либо применяет цены,<br>либо отправляет товар в карантин.
              Market -->>- Merchant: OK
          end

          rect rgb(251, 243, 232)
              note right of Merchant: Проверка, не попал ли какой товар в карантин
              Merchant ->> Market: POST v2/businesses/{businessId}/price-quarantine
              Market -->> Merchant: OK: список товаров в карантине.
              alt Карантин не пустой, и в ценах есть ошибки
                  Merchant ->>+ Market: Исправленные цены<br>POST v2/businesses/{businessId}/offer-prices/updates
                  Market ->> Market: Проверяет<br>и устанавливает цены.
                  Market -->>- Merchant: OK
              else Карантин не пустой, но все цены правильные
                  Merchant ->>+ Market: POST v2/businesses/{businessId}/price-quarantine/confirm
                  Market ->> Market: Убирает товары<br>из карантина.
                  Market -->>- Merchant: OK
              end
          end
    ```
    <!-- endsource: ru/_includes/mermaid/assortment-price.md -->

    1. Чтобы узнать стоимость услуг Маркета для конкретных товаров, передайте их параметры в запросе [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md).
    1. Передайте новые цены для конкретного магазина с помощью запроса [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md).

        [Как получить установленные цены](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/getPricesByOfferIds.md)
    1. Убедитесь, что ни один из товаров не попал в карантин с помощью запроса [POST v2/campaigns/{campaignId}/price-quarantine](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/getCampaignQuarantineOffers.md).
    1. Если карантин не пустой, проверьте цены на товары. Ошибочно установленные цены для конкретного магазина можно исправить запросом [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md).
    1. После того как в карантине останутся только правильные цены, подтвердите их запросом [POST v2/campaigns/{campaignId}/price-quarantine/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmCampaignPrices.md). Если ложные срабатывания карантина случаются часто, подумайте о том, чтобы изменить его порог по [инструкции](https://yandex.ru/support/marketplace/assortment/operations/prices.html#quarantine).

{% endlist %}
