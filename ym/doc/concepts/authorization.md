---
title: Авторизация
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/authorization.md"
fetched_at: "2026-09-24T02:13:00Z"
content_sha: bb28c627531d9c77
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/authorization.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/authorization.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/authorization.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/concepts/authorization.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Авторизация

Чтобы работать с Маркетом через API, нужно получить API-Key-токен. Не рекомендуем использовать OAuth-токен, так как этот способ авторизации устарел.

{% note info "Нужно ли немедленно переходить на Api-Key-токен?" %}

Вы можете использовать уже сгенерированный OAuth-токен до конца его срока действия или сразу перейти на работу с API-Key-токеном. 

[Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)

В период перехода с одного токена на другой вы можете передавать оба:
   * [Как передавать API-Key-токен](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md#use)
   * [Как передавать OAuth-токен](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md#use)

{% endnote %}

## Токены API Маркета {#token-types}

#|
||  | [**Api-Key**](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | [**OAuth**](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md) (устаревший) ||

|| **Привязка** | К кабинету, в котором создан токен. | К пользователю, который создал токен. ||

|| **Способ получения** | В кабинете продавца на Маркете. [Инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)

| Через создание OAuth-приложения. [Инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md)||

|| **Доступ к магазинам** | Все магазины в кабинете. | Только к тем, к которым у пользователя есть доступ. ||

|| **Можно ли настроить доступ к определенным группам методов** | Да. [Инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)| Нет. ||

|| **Заголовок для передачи** | `Api-Key`. [Как передавать токен](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md#use)

| `Authorization`. [Как передавать токен](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md#use)||

|| **Срок действия токена** | Неограничен. | 1 год. ||

|#
