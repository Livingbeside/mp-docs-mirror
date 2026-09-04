---
title: Вызов методов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/method-call.md"
fetched_at: "2026-09-04T01:57:39Z"
content_sha: f41424cb02cf6aaf
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/method-call.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/method-call.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/method-call.md
  - href: ru/concepts/method-call.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Вызов методов

Запросы к API Яндекс Маркета передаются по протоколу HTTPS, таймаут — 10 секунд, Keep-Alive не поддерживается.

```no-highlight translate=no
<http_method> https://api.partner.market.yandex.ru/<version>/<resource>.<format>?<query_parameters>
```

Где:
- `<http_method>` ― DELETE, GET, POST или PUT.
- `<version>` ― версия конкретного метода (v1, v2, v3, ...).
  - Версии разных методов независимы.
  - Актуальная версия указана на странице этого метода.
  - Версия указывается в пути URL и является обязательной.

    {% note warning "Обязательно указывайте версию, если не делали этого раньше" %}

    Скоро мы отключим возможность работать с запросами без указания версии.

    {% endnote %}

- `<resource>` ― URL ресурса, над которым выполняется действие. Названия ресурсов приведены в описании соответствующих методов.

    Здесь передаются параметры пути (path parameters) — данные, которые отличаются в зависимости от магазина или кабинета.

    {% cut "Пример" %}

    ```no-highlight translate=no
    https://api.partner.market.yandex.ru/v2/campaigns/{campaignId}
    ```

    `/{campaignId}` — параметр пути, где вы указываете свой идентификатор кампании.

    {% endcut %}

- `<format>` ― это необязательная часть запроса, которая влияет на способ представления ответа. Формат ответа может быть указан в HTTP-заголовке `Accept`. Данные передаются в формате JSON. В описании каждого метода приведены примеры запросов и ответов.
- `<query_parameters>` ― обязательные и необязательные параметры запроса.

    Здесь передается ключ и его значение, которые нужны для уточнения запроса, фильтрации и сортировки входящей информации, пагинации.

    Параметры запроса отделяются от URL ресурса вопросительным знаком, а между парами «ключ-значение» используется амперсанд (&).

    {% cut "Пример" %}

    ```no-highlight translate=no
    https://api.partner.market.yandex.ru/v2/reports/shows-boost/generate?format=CSV
    ```

    `?format=CSV` — параметр запроса.

    {% endcut %}

**Для продавцов Market Yandex Go:** также прочтите [инструкцию](https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md#method-call).

Если произошла ошибка, прекращается обработка запроса и возвращается информация о ней. [Типы ошибок и что с ними делать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)


### Как работает версионирование методов {#how-versioning-works}

Версия относится к конкретному методу. Разные методы могут иметь разные актуальные версии (например, один — v1, другой — v3).

#### Примеры одного и того же метода в разных версиях

```no-highlight translate=no
GET https://api.partner.market.yandex.ru/v1/campaigns
GET https://api.partner.market.yandex.ru/v2/campaigns
```

Здесь `v1` и `v2` — версии одного и того же метода `.../campaigns`. Они могут отличаться составом полей, правилами валидации и доступными параметрами.

{% note info "Примечание" %}

Версия метода `GET /v1/campaigns` снята с поддержки и недоступна.

{% endnote %}

#### Как выбрать и зафиксировать версию

- Откройте страницу нужного метода в документации — там указана актуальная версия и статус предыдущих.
- Фиксируйте конкретную версию в клиенте и URL (не используйте «последнюю по умолчанию»).
- Отслеживайте объявления о новых версиях и планах вывода старых из эксплуатации на странице метода.

#### Миграция между версиями

1. Изучите изменения на странице метода (что добавлено/изменено/удалено).
2. Обновите схему запросов/ответов и параметры под новую версию.
3. Протестируйте свои изменения.
4. Переключите версию в URL на новую.
5. Мониторьте ошибки и метрики; при необходимости временно вернитесь на прежнюю версию.

#### Частые вопросы

- Что будет, если указать несуществующую версию?
  — Вернётся ошибка [`404 Not Found`](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md#404). Указывайте строчную букву `v`, заглавная `V` так же приведёт к ошибке `404`.
- Где посмотреть, какая версия используется сейчас?
  — В URL вашего запроса: сегмент `v1`/`v2`/`v3` в пути.
- Меняется ли версия у всех методов разом?
  — Нет. Каждый метод версионируется независимо.
