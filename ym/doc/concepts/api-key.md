---
title: Api-Key
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md"
fetched_at: "2026-09-04T01:57:32Z"
content_sha: f55d1a3ffdfc48f4
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/api-key.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/api-key.md
  - href: ru/concepts/api-key.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Создание и использование API-Key-токена

Чтобы работать с Маркетом через API:

1. Создайте токен с доступами к определенным группам методов. Так сотрудники смогут вызывать только те методы, которые нужны им для работы. [Какие бывают доступы](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/access.md)
2. Вставьте токен в заголовок запроса к Маркету.

Создавать токены и управлять ими может только владелец кабинета и менеджер кабинета. Подробнее о том, какие бывают роли, читайте [в Справке Маркета для продавцов](https://yandex.ru/support2/marketplace/ru/account/permissions/roles).

Максимальное количество токенов для кабинета — 30.

Токен действует бессрочно — он остается активным до тех пор, пока вы его не удалите.

## Создать токен {#new-token}

1. В кабинете продавца на Маркете нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**.

1. В блоке **Токены авторизации** нажмите кнопку **Создать новый токен**.

    ![Скриншот](../_images/concepts/api-token.png)

1. В открывшемся окне:

    1. Укажите уникальное название токена.

    1. Выберите доступы, которые нужно предоставить.

    1. Нажмите кнопку **Создать**.

    ![Скриншот](../_images/concepts/access.png)

## Редактировать токен {#edit-token}

{% note warning "Перед редактированием" %}

Убедитесь, что ваша интеграция продолжит работать с измененным токеном.

{% endnote %}

Вы можете изменить доступы, а также название токена. Для этого:

1. В кабинете продавца на Маркете нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**.

1. В блоке **Токены авторизации** найдите нужный, нажмите три точки рядом с ним и выберите **Редактировать**.

1. Измените необходимую информацию.

1. Нажмите **Сохранить**.

Информация обновится в течение 10 минут.

## Удалить токен {#delete-token}

{% note warning "Перед удалением" %}

Убедитесь, что без этого токена ваша интеграция продолжит работать.

{% endnote %}

1. В кабинете продавца на Маркете нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули**.

1. В блоке **Токены авторизации** найдите нужный, нажмите три точки рядом с ним и выберите **Удалить**.

1. Подтвердите удаление.

## Передать токен {#use}

Полученный токен вставьте в заголовок `Api-Key` по следующей схеме:

```no-highlight translate=no
Api-Key: <token>
```

В результате заголовок будет выглядеть так:

```no-highlight translate=no
Api-Key: ACMA:I4c4CxCSYaI41RSC2uYWP2qj3Rhhm4knMiBEga5K:151c0664
```

Если запрос придет без заголовка с действительным токеном, Маркет вернет ошибку `401 Unauthorized`.

## Может быть полезно {#read-more}

* [Метод получения информации о переданном токене авторизации](https://yandex.ru/dev/market/partner-api/doc/ru/reference/auth/getAuthTokenInfo.md)
* [Описание ошибок, возвращаемых API Маркета](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md)
