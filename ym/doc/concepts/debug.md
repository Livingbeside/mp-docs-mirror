---
title: Логи запросов
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md"
fetched_at: "2026-08-28T11:51:21Z"
content_sha: b949155b01f6a510
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/debug.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/debug.md
  - href: ru/concepts/debug.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Логи запросов

На страницах с логами вы можете посмотреть запросы к API Маркета или API магазина, а также узнать информацию по ответу. Для этого в кабинете продавца на Маркете нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули** → вкладка **Лог запросов** или **Лог уведомлений**.

![Скриншот виджета](../_images/concepts/widget.png)

{% note warning %}

Если API недоступно, запросы к API не выполняются и не записываются в логи. [Подробнее об управлении доступом к API](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md)

{% endnote %}

На этих страницах по каждой интеграции есть виджеты с информацией:

   * вызовы к каким ресурсам завершаются c ошибками (вкладка **Лог запросов**);

   * ответ на какой тип уведомления приходит с ошибкой (вкладка **Лог уведомлений**);
   * процент и количество ошибок в запросах.

Для корректной работы интеграции исправьте ошибки. Чтобы посмотреть детали, нажмите на строку с проблемным запросом или типом уведомления, таблица с логами обновится.

  ![Скриншот таблицы логов](../_images/concepts/logs.png)

## Как работать с логами {#how-to}

На странице логов вы можете:

 * Искать по телу запроса и ответа, а также по параметрам запроса. Для этого в поле **Поиск** введите информацию, которую хотите найти.

 * Искать по фильтрам. Например, с помощью фильтра **Ресурс** вы можете находить запросы по определенным методам, а по фильтру **Интеграция** — запросы, которые относятся к выбранной интеграции.

 * Смотреть подробную информацию по запросу — нажмите на строку с ним, чтобы увидеть сам запрос и полученный ответ. Подробнее об ошибках и как их решать:

   * [Ошибки запросов к API Маркета](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)
   * [Ошибки при подключении или работе с API-уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/error-codes.md)

 * Проверять, к какой интеграции относятся запросы и ответы, — в блоке **Тип интеграций** указано название, которое вы передали в запросе или ответе, или тип **Консоль документации**, если вы использовали ее. [Подробнее о том, как подписывать интеграции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/integration-signing.md)

## Уникальный идентификатор запроса {#traceparent}

Маркет передает уникальный идентификатор запроса в заголовке [traceparent](*traceparent):

* ответа, если это запрос магазина к Маркету;
* самого запроса в случае API-уведомлений, когда Маркет отправляет запрос магазину. [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)

Пример заголовка запроса или ответа:

```no-highlight translate=no
Content-Type: application/json
traceparent: 00-8b05ba11f1d37f7cfce0eac1a5230600-8b23fad39202f968-01
```

С идентификатором запроса вы быстрее найдете его логи, а также он может пригодиться при обращении в поддержку.

Чтобы найти информацию по выполненному запросу:

1. Вставьте уникальный идентификатор в поле **Поиск**.

2. Нажмите на запрос, чтобы увидеть подробную информацию, в том числе его идентификатор в поле **Трассировка**.

[*traceparent]:
Входит в открытый стандарт [OpenTelemetry](https://opentelemetry.io/docs/).
