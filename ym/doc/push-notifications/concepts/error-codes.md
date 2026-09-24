---
title: Сообщения об ошибках
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/error-codes.md"
fetched_at: "2026-09-24T02:15:03Z"
content_sha: 786fb0c229e49e97
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/push-notifications/concepts/error-codes.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/error-codes.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/push-notifications/concepts/error-codes.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/error-codes.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Сообщения об ошибках

Когда Маркет отправляет запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md), верните ответ с кодом `200` и информацией об обработке уведомления. [Тело ответа](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md#200-ok)

Если есть ошибка, сообщите о ней:

* `400 Bad Request` — Маркет прислал некорректное уведомление. В ответе укажите тип ошибки и опишите ее. [Тело ответа](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md#400-bad-request)

* `500 Internal Server Error` — ошибка на стороне магазина. [Тело ответа](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md#500-internal-server-error)

Передача других кодов будет считаться ошибкой, как при ответе кодом `500`. [API магазина не отвечает](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md#no-answer)


## Ошибки при подключении или работе с API-уведомлениями {#shop-errors}

**Тип ошибки**|**Подтип ошибки**|**Описание ошибки**
----- | ----- | -----
`CANT_GET_RESPONSE` | `CONNECTION_REFUSED` | Не удалось установить соединение с сервером магазина. Ошибка может быть вызвана сетевыми проблемами на стороне магазина.
`CANT_GET_RESPONSE` | `CONNECTION_TIMED_OUT` | Истекло время ожидания подключения к серверу магазина.
`CANT_GET_RESPONSE` | `HTTP` | От магазина поступил ответ, отличный от `200 OK`.
`CANT_GET_RESPONSE` | `READ_TIMED_OUT` | Истекло время ожидания ответа магазина на запрос Маркета.
`CANT_GET_RESPONSE` | `SSL_ERROR` | Не удается установить безопасное соединение с сервером магазина. Сертификат безопасности не действителен.
`CANT_GET_RESPONSE` | `UNSUPPORTED_MEDIA_TYPE` | В заголовке ответа магазина указан формат данных, отличный от `application/json`. [Формат данных](data-format.md)
`INVALID_RESPONSE` | `CANT_PARSE_RESPONSE` | Не удалось извлечь данные из ответа магазина.
`INVALID_RESPONSE` | `INVALID_DATA` | В теле ответа магазина переданы некорректные данные или их недостаточно. Например, отсутствует информация о версии интеграции.

Подробную информацию по запросам и ответам, в том числе ошибки, можно посмотреть в кабинете продавца на Маркете — нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули** → вкладка **Лог уведомлений**. Подробнее об этом читайте в разделе [Логи запросов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/debug.md).
