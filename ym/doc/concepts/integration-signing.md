---
title: Подпись интеграций
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/integration-signing.md"
fetched_at: "2026-09-24T02:13:13Z"
content_sha: 301ca02cd98fb9d5
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/integration-signing.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/integration-signing.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/integration-signing.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/concepts/integration-signing.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Как подписывать интеграции

В кабинете продавца на Маркете на странице **API и модули** на вкладке **Лог запросов** вы можете посмотреть информацию по запросам и ответам, а также по проблемам, которые с ними связаны. Чтобы понять, к какой интеграции относятся данные, необходимо подписывать:

* **Запросы**, которые вы отправляете к API Маркета, — в заголовке передайте название интеграции и ее версию, если она есть. 
    
    Формат: `X-Market-Integration: название интеграции/версия`. 
    
    Например, `X-Market-Integration: Bitrix` или `X-Market-Integration: Bitrix/1.0.0`.

* **Ответы** на [API-уведомления](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) от Маркета — передайте название интеграции и ее версию в ответе на запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) в параметрах `name` и `version`.

Название интеграции отображается на странице **Лог запросов** в блоке **Тип интеграций**. Также на этой странице вы можете использовать фильтр **Интеграция**. [Подробнее о работе с логами](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md)

**Требования к названию:**

* Максимальное количество символов — 100.
* Только ASCII символы из [таблицы](https://www.ascii-code.com/compact).
