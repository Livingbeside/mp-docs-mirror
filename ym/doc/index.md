---
title: index.md
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/index.md"
fetched_at: "2026-09-22T02:26:09Z"
content_sha: d627df547e67ebf7
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.0
alternate:
  - en/
  - ru/
  - zh/
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/index.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# API Яндекс Маркета для продавцов

API Маркета помогает продавцам управлять ассортиментом и ценами, обрабатывать заказы, обновлять остатки и решать множество других задач.

## Как настроить интеграцию {#start}

1. Прочитайте страницу [Создание и использование API-Key-токена](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md). Там рассказано, как авторизоваться для доступа к ресурсам.
1. Прочитайте [инструкцию по подключению OpenAPI-спецификации](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/openapi.md).
1. **Для продавцов Market Yandex Go:** прочитайте инструкцию [Как работать с API Маркета](https://yandex.ru/dev/market/partner-api/doc/ru/market-yandex-go-sellers.md).
1. Посмотрите раздел [Пошаговые инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/index.md) — если там есть инструкция для вашей задачи, начните с нее.
1. Откройте [обзор методов API](https://yandex.ru/dev/market/partner-api/doc/ru/overview/index.md) для нужной модели и выберите те, что нужны для решения задачи.
1. Прочитайте детальное описание каждого метода и реализуйте интеграцию.
1. При необходимости подключите API-уведомления и Маркет отправит вам запрос с информацией о [событии](*notification-type), когда оно произойдет. 
    
    Это необязательная интеграция. Однако с помощью уведомлений вы сможете оперативно реагировать на изменения в заказах, невыкупах и возвратах, а также на появление заявки на отмену заказа.
    
    [Как подключить API-уведомления](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md#how-to-start)

[*notification-type]: События, по которым Маркет присылает уведомления:<ul><li>создание нового заказа;</li><li>изменение заказа;</li><li>изменение статуса заказа;</li><li>создание нового чата с покупателем;</li><li>добавление нового сообщения в чате;</li><li>начало спора;</li><li>завершение спора;</li><li>создание нового отзыва о товаре;</li><li>создание нового комментария к отзыву;</li><li>создание заявки на отмену заказа;</li><li>отмена заказа;</li><li>создание нового невыкупа или возврата;</li><li>изменение статуса невыкупа или возврата.</li></ul>Уведомления будут приходить в том числе и по тестовым заказам.
