---
title: Настройка интеграции с нуля на JavaScript
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/quick-start-js.md"
fetched_at: "2026-09-24T02:13:15Z"
content_sha: 01fad945350e0fb5
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/step-by-step/quick-start-js.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/quick-start-js.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/step-by-step/quick-start-js.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/quick-start-js.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Запуск интеграции на JavaScript

Эта инструкция поможет с нуля настроить простейшую тестовую интеграцию на языке JavaScript для запросов магазина к Маркету. Вы сможете запросить список магазинов и получить ответ.

{% note info "Вам понадобится Node.js и Java не ниже 11-й версии" %}

Установите их заранее.

[Как установить Node.js](https://nodejs.org/en)

[Как установить Java](https://www.java.com/ru/download/help/download_options.html)

{% endnote %}

## Скачайте OpenAPI-спефицикацию {#download}

{% list tabs %}

- Через git

  1. Откройте папку, в которой хотите сохранить спецификацию. В этой инструкции она будет обозначаться как `<project_directory>`.
  2. Запустите в ней командную строку.
  3. Напишите команду:

        ```no-highlight translate=no
        git clone https://github.com/yandex-market/yandex-market-partner-api.git
        ```

- Просто браузером

  1. Скачайте [спецификацию Маркета с GitHub](https://github.com/yandex-market/yandex-market-partner-api/archive/refs/heads/main.zip).
  2. Распакуйте архив в папку, в которой хотите сохранить спецификацию. В этой инструкции она будет обозначаться как `<project_directory>`.

{% endlist %}

## Сгенерируйте клиент {#generate}

1. Откройте папку `yandex-market-partner-api`, которая появилась на предыдущем шаге.
2. Запустите в ней командную строку.
3. Напишите команду:

```text translate=no
npx @openapitools/openapi-generator-cli generate -i <path_to_openapi.yaml> -g javascript -o <output_path>
```

В качестве **output path** укажите папку, в которой будет ваш проект.

Если **openapitools** пока не установлено, согласитесь на установку. В папке **output path** появятся файлы клиента.

> **Пример**
>
> Допустим, вы скачали архив и распаковали его. Спецификация лежит в папке `<project_directory>/yandex-market-partner-api`.
>
> Вы хотите разместить проект в папке `<project_directory>/market-integration`.
>
> &#49;. Откройте папку `<project_directory>/yandex-market-partner-api`.
>
> &#50;. Запустите в ней командную строку.
>
> &#51;. В открывшуюся консоль напишите:
>
>    ```text translate=no
>    npx @openapitools/openapi-generator-cli generate -i openapi/openapi.yaml -g javascript -o ../market-integration
>    ```
>
> &#52;. Если появится предложение установить генератор, введите **Y** и нажмите **Enter**.


## Создайте проект {#create-project}

1. Откройте папку, в которой лежат файлы клиента. В примере выше это `<project_directory>/market-integration`.
2. Запустите в ней командную строку.
3. Напишите команду:

    ```text translate=no
    npm install
    npm run build
    ```

## Подготовьте данные для доступа {#token}

Получите токен авторизации по [инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md).

## Выполните запрос {#code}

Чтобы выполнить [GET v2/campaigns](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaigns.md):

1. Откройте в IDE созданный проект.
2. Создайте в корне проекта (папке `<project_directory>/market-integration`) файл `index.js`.
3. Создайте экземпляр `CampaignsApi` и обратитесь к методу `getCampaigns`. Для этого напишите в `index.js` вот такой код:

    ```javascript translate=no
    const { CampaignsApi } = require('./dist');

    const campaignsApi = new CampaignsApi();
    campaignsApi.apiClient.authentications['ApiKey'].apiKey = '<token>';

    campaignsApi.getCampaigns(undefined, function (error, data) {
        console.log(JSON.stringify(data, null, 4));
    });
    ```

    В качестве `<token>` используйте токен, который получили на предыдущем шаге.

4. В консоль напишите `node index.js`.

В консоли отобразится результат запроса: названия всех магазинов, модели размещения, идентификаторы и прочее:

```json translate=no
{
    "campaigns": [
        {
            "domain": "Shop 1",
            "id": 12345678,
            "clientId": 87654321,
            "business": {
                "id": 123456,
                "name": "My shop"
            },
            "placementType": "FBS"
        },
        {
            "domain": "Shop 2",
            "id": 23456789,
            "clientId": 98765432,
            "business": {
                "id": 123456,
                "name": "My shop"
            },
            "placementType": "DBS"
        },
        {
            "domain": "GoodShop",
            "id": 34567891,
            "clientId": 19876543,
            "business": {
                "id": 123456,
                "name": "My shop"
            },
            "placementType": "FBY"
        },
    ],
    "pager": {
        "total": 3,
        "from": 1,
        "to": 3,
        "currentPage": 1,
        "pagesCount": 1,
        "pageSize": 3
    }
}
```
