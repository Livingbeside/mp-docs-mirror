---
title: OAuth 2.0 (устаревший)
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md"
fetched_at: "2026-08-28T11:51:17Z"
content_sha: 1a61b7212afcc265
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/oauth-2.0.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/oauth-2.0.md
  - href: ru/concepts/oauth-2.0.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

{% note warning "Авторизация по OAuth-токену" %}

Не рекомендуем использовать OAuth-токен, так как этот способ авторизации устарел.

Вы можете использовать уже сгенерированный токен до конца его срока действия или создать API-Key-токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)

{% endnote %}

# Создание и использование OAuth-токена

Для авторизации используется протокол OAuth 2.0. Чтобы работать с Маркетом через API:

1. Создайте приложение на сайте oauth.yandex.ru. Если у вас уже есть приложение с доступом `market:partner-api`, создавать новое не нужно — можно использовать одно для всех магазинов и бизнес-аккаунтов.
1. Создайте токен на имя сотрудника, который имеет доступ к данным магазина.
1. Вставьте токен в заголовки запросов к Маркету.

## Создать приложение {#application}

1. Войдите в аккаунт на Яндексе, от имени которого ваша система будет обращаться к API Маркета.

   {% note warning "Отнеситесь внимательно к выбору аккаунта" %}

   Это должен быть аккаунт:

      * К которому бизнес не потеряет доступ.
      * Который не потеряет доступ к бизнесу — например, при увольнении сотрудника.

   <br>
   Лучше всего использовать аккаунт, защищенный двухфакторной аутентификацией и принадлежащий владельцу бизнеса.
   <br><br>

   **Токен нужно будет получать снова**

   Если пользователь Яндекс ID, который его создал:
      * выйдет со всех устройств в аккаунте Яндекса;
      * изменит пароль;
      * включит или выключит двухфакторную аутентификацию;
      * восстановит доступ.

   Подробнее об отзыве токена читайте в [Справке Яндекс ID](https://yandex.ru/dev/id/doc/ru/tokens/token-invalidate).

   {% endnote %}

1. Откройте страницу **[oauth.yandex.ru/client/new/api](https://oauth.yandex.ru/client/new/api)**. ⚠️ Пользуйтесь именно этой ссылкой. Если просто нажать кнопку создания приложения на сайте Яндекс ID, ничего не получится.
1. В поле **Название вашего сервиса** напишите что угодно. Если у вас много приложений и вам важно в них ориентироваться, впишите название бизнеса.
1. Укажите почту для связи.
1. В поле **Доступ к данным** введите `market:partner-api` и выберите **API Яндекс.Маркета / Поиска по товарам для партнеров** в выпадающем списке.

      {% note info "Почему мне не видно поле «Доступ к данным»?" %}

      Вероятно, вы не перешли по ссылке **[oauth.yandex.ru/client/new](https://oauth.yandex.ru/client/new)**, а нажали кнопку создания приложения на сайте Яндекс ID. Вам нужна именно та форма создания приложения, которая открывается по ссылке.

      {% endnote %}

1. Нажмите **Создать приложение**.
1. Пройдите верификацию с помощью вашего аккаунта на Госуслугах.

## Создать токен {#token}

После создания приложения нужно получить токен.

{% note info "Можно ли для получения токена использовать не тот же самый аккаунт, который использовали для создания приложения?" %}

Можно. Он тоже должен соответствовать тем же требованиям. Если Яндекс ID, на который оформлен токен, потеряет доступ к бизнесу, API перестанет работать.

{% endnote %}

1. Откройте [oauth.yandex.ru](https://oauth.yandex.ru/) и нажмите на созданное приложение для доступа к Маркету.
1. Скопируйте **ClientID** этого приложения.
1. Вставьте индентификатор в эту ссылку:

   ```no-highlight translate=no
   https://oauth.yandex.ru/authorize?response_type=token&client_id=<ClientID>
   ```

   Получится примерно так:

   ```no-highlight translate=no
   https://oauth.yandex.ru/authorize?response_type=token&client_id=5473335а275a5nb8e2648q12n8r378l7
   ```

1. Перейдите по получившейся ссылке. Если появилось окно **Сервис ещё не верифицирован**, пройдите верификацию с помощью вашего аккаунта на Госуслугах.
1. Подтвердите вход.
1. Скопируйте токен.

{% note warning "Такой токен действует год" %}

Когда год подойдет к концу, создайте API-Key-токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md)

{% endnote %}

## Передать токен {#use}

Полученный токен вставьте в заголовок `Authorization` по следующей схеме:

```no-highlight translate=no
Authorization: Bearer <token>
```

В результате заголовок будет выглядеть так:

```no-highlight translate=no
Authorization: Bearer y0_BfRRRRRV2L8sWWvNkSNNNNSrLHaNXg4cCMswFbL6MWab9lktL2KPsMw
```

Если запрос придет без заголовка с действительным токеном, Маркет вернет ошибку `401 Unauthorized`.

{% note info "Расширенные возможности API по подписке" %}

Для работы с расширенными возможностями API по [подписке](https://yandex.ru/support/marketplace/ru/marketing/subscription) при использовании авторизации по OAuth-токену необходимо передавать бизнес ID в заголовке `X-Business-Id`:

```no-highlight translate=no
X-Business-Id: <business_id>
```

{% endnote %}

## Может быть полезно {#read-more}

* [Справка авторизационного сервиса Яндекс ID](https://yandex.ru/dev/id/doc/ru/)
* [Описание ошибок, возвращаемых API Маркета](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)
