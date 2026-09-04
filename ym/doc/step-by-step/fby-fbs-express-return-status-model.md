---
title: Статусы FBY-, FBS- и Экспресс-возвратов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fby-fbs-express-return-status-model.md"
fetched_at: "2026-09-04T01:57:53Z"
content_sha: cc7a916fb287f63e
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/fby-fbs-express-return-status-model.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/fby-fbs-express-return-status-model.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/fby-fbs-express-return-status-model.md
  - href: ru/step-by-step/fby-fbs-express-return-status-model.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

## Как изменяются статусы возвратов для моделей FBY, FBS и Экспресс

<!-- source: ru/_includes/mermaid/fby-fbs-express-return-status-graph.md -->
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
    UserCreation(Покупатель создал возврат) -->|Решение по возврату не нужно| StartedByUser[STARTED_BY_USER]
    StartedByUser[STARTED_BY_USER] -->|Можно возвращать деньги| RefundInProgress[REFUND_IN_PROGRESS]
    RefundInProgress[REFUND_IN_PROGRESS] -->|Деньги возвращены| Refunded[REFUNDED]
    StartedByUser[STARTED_BY_USER] -->|Возврат отклонен арбитром или в ПВЗ| Rejected[REJECTED]

    UserCreation(Покупатель создал возврат) -->|Ожидается решение по возврату| PremoderationDecisionWaiting[PREMODERATION_DECISION_WAITING]
    PremoderationDecisionWaiting[PREMODERATION_DECISION_WAITING] --> |Решение принято| PremoderationDecisionMade[PREMODERATION_DECISION_MADE]
    PremoderationDecisionWaiting[PREMODERATION_DECISION_WAITING] --> |Время на принятие решения вышло, возврат подтвержден| PremoderationSelectDelivery[PREMODERATION_SELECT_DELIVERY]
    PremoderationDecisionMade[PREMODERATION_DECISION_MADE] --> |Магазин согласился с возвратом| PremoderationSelectDelivery[PREMODERATION_SELECT_DELIVERY]
    PremoderationDecisionMade[PREMODERATION_DECISION_MADE] --> |Покупатель не согласился с решением| PremoderationDispute[PREMODERATION_DISPUTE]

    PremoderationDispute[PREMODERATION_DISPUTE] --> |Арбитр отклонил возврат| Rejected[REJECTED]
    PremoderationDispute[PREMODERATION_DISPUTE] --> |Спор решен, покупатель получает возврат денег| PremoderationSelectDelivery[PREMODERATION_SELECT_DELIVERY]
    PremoderationDecisionMade[PREMODERATION_DECISION_MADE] --> |Возврат отклонен, покупатель его не обжаловал| Rejected[REJECTED]
    PremoderationSelectDelivery[PREMODERATION_SELECT_DELIVERY] --> |Покупатель выбрал способ доставки| StartedByUser[STARTED_BY_USER]

```
<!-- endsource: ru/_includes/mermaid/fby-fbs-express-return-status-graph.md -->
