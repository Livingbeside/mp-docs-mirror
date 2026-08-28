---
title: Формат ответов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/result-format.md"
fetched_at: "2026-08-28T11:51:18Z"
content_sha: 1d7778d8979d2729
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/result-format.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/result-format.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/result-format.md
  - href: ru/concepts/result-format.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Формат ответа

API Яндекс Маркета возвращает ответы в кодировке UTF-8. Ответы могут быть только в формате JSON.

Чтобы задать формат ответа, необходимо указать в URL запроса выбранный формат после имени метода. Например, в результате выполнения следующего запроса вы получите список товаров в каталоге в формате JSON:

```no-highlight translate=no
GET https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}/offer-mapping-entries.json
```

Также формат ответа можно задать при вызове методов с помощью HTTP-заголовка `Accept`. Возможное значение заголовка: `application/json`.

Формат ответа должен совпадать с [форматом входных данных](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/input-format.md). Поэтому в заголовке `Accept` или в URL запроса (расширение `.json` ) задавайте такой же формат, как и в заголовке `Content-Type`.

При вызове DELETE-методов формат результата необходимо указывать, чтобы обеспечить совместимость с библиотеками, которые используются для работы с данными.

{% note info "Некоторые системы Маркета убирают пробелы в начале и в конце строки" %}

Например, строка `" пример "` может быть сохранена как `"пример"`.

Если у вас есть строки с такими пробелами, учитывайте эту особенность. Например, удаляйте пробелы перед передачей строк Маркету и перед сверкой данных.

{% endnote %}
