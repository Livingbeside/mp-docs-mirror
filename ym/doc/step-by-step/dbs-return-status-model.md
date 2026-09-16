---
title: Статусы DBS-возвратов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/dbs-return-status-model.md"
fetched_at: "2026-09-16T02:26:56Z"
content_sha: 52cc84fda61fa402
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.4
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/dbs-return-status-model.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/dbs-return-status-model.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/dbs-return-status-model.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/dbs-return-status-model.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

## Как изменяются статусы возвратов для модели DBS

<!-- source: ru/_includes/mermaid/dbs-return-status-graph.md -->
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
    UserCreation(Покупатель создал возврат) --> StartedByUser[STARTED_BY_USER]
    StartedByUser[STARTED_BY_USER] -->|Ожидается решения по возврату| WaitingForDecision[WAITING_FOR_DECISION]
    WaitingForDecision[WAITING_FOR_DECISION] -->|Решение принято| DecisionMade[DECISION_MADE]
    WaitingForDecision[WAITING_FOR_DECISION] -->|Время на принятие решения вышло, возврат подтвержден| RefundInProgress[REFUND_IN_PROGRESS]
    DecisionMade[DECISION_MADE] -->|Можно возвращать деньги| RefundInProgress[REFUND_IN_PROGRESS]
    DecisionMade[DECISION_MADE] -->|Покупатель не согласился с решением, но арбитр отклонил возврат| Rejected[REJECTED]
    RefundInProgress[REFUND_IN_PROGRESS] -->|Деньги возвращены| Refunded[REFUNDED]
    StartedByUser[STARTED_BY_USER] -->|Возврат отклонен арбитром или в ПВЗ| Rejected[REJECTED]
```
<!-- endsource: ru/_includes/mermaid/dbs-return-status-graph.md -->
