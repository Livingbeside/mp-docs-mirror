---
title: Интеграция на Node.js Express
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/quick-start-notifications-node-express.md"
fetched_at: "2026-08-28T11:53:27Z"
content_sha: 0a4796a5fe3329ab
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/push-notifications/concepts/quick-start-notifications-node-express.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/concepts/quick-start-notifications-node-express.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/push-notifications/concepts/quick-start-notifications-node-express.md
  - href: ru/push-notifications/concepts/quick-start-notifications-node-express.md
    type: text/markdown
    title: Markdown version
  - href: ../../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Запуск интеграции на Node.js Express

Эта инструкция поможет с нуля настроить простейшую тестовую интеграцию на языке JavaScript для работы с уведомлениями. Вы сможете проверить, обрабатывает ли ваш сервер уведомление.

{% note info "Вам понадобится Node.js и Java не ниже 11-й версии, а также Curl для проверки работы сервера" %}

Установите их заранее. Как установить:

* [Node.js](https://nodejs.org/en)

* [Java](https://www.java.com/ru/download/help/download_options.html)

* [Curl](https://curl.se/download.html)

{% endnote %}

## Скачайте OpenAPI-спефицикацию {#download}

{% list tabs %}

- Через git

  1. Откройте папку, в которой хотите сохранить спецификацию. В этой инструкции она будет обозначаться как `<project_directory>`.
  1. Запустите в ней командную строку.
  1. Напишите команду:

        ```no-highlight translate=no
        git clone https://github.com/yandex-market/yandex-market-notification-api.git
        ```

- Просто браузером

  1. Скачайте [спецификацию сервиса уведомлений Маркета с GitHub](https://github.com/yandex-market/yandex-market-notification-api/archive/refs/heads/main.zip).
  1. Распакуйте архив в папку, в которой хотите сохранить спецификацию. В этой инструкции она будет обозначаться как `<project_directory>`.

{% endlist %}

## Сгенерируйте сервер {#generate}

1. Откройте папку `yandex-market-notification-api`, которая появилась на предыдущем шаге.
1. Запустите в ней командную строку.
1. Напишите команду:

    ```text translate=no
    npx @openapitools/openapi-generator-cli generate -i <path_to_openapi.yaml> -g nodejs-express-server -o <output_path>
    ```

В качестве **output path** укажите папку, в которой будет ваш проект.

Если **openapitools** пока не установлено, согласитесь на установку. В папке **output path** появятся файлы клиента.

{% note info "Подробнее о генераторе nodejs-express-server" %}

Документация по генератору: [nodejs-express-server](https://openapi-generator.tech/docs/generators/nodejs-express-server)

{% endnote %}

> **Пример**
>
> Допустим, вы скачали архив и распаковали его. Спецификация лежит в папке `<project_directory>/yandex-market-notification-api`.
>
> Вы хотите разместить проект в папке `<project_directory>/market-integration`.
>
> &#49;. Откройте папку `<project_directory>/yandex-market-notification-api`.
>
> &#50;. Запустите в ней командную строку.
>
> &#51;. В открывшуюся консоль напишите:
>
>        ```
>        npx @openapitools/openapi-generator-cli generate -i openapi/openapi.yaml -g nodejs-express-server -o ../market-integration
>        ```
>
> &#52;. Если появится предложение установить генератор, введите **Y** и нажмите **Enter**.

## Реализуйте обработку уведомления {#code}

1. Откройте в IDE директорию со сгенерированным кодом.
1. В `services/NotificationService.js` находится логика обработки уведомлений. Добавьте туда простой код для обработки уведомления с типом `PING`:

    ```javascript translate=no
    const Service = require('./Service');
    const logger = require('../logger');

    const sendNotification = (sendNotificationRequest) => new Promise(
      async (resolve, reject) => {
        try {
          if (sendNotificationRequest.body.notificationType == 'PING') {
            logger.info("PING notification processed")
          }
          // Возвращаем обязательное тело ответа
          resolve(Service.successResponse({
            name: "shop",
            time: new Date().toISOString(),
            version: "1.0.0"
          }));
        } catch (e) {
          reject(Service.rejectResponse(
            e.message || 'Invalid input',
            e.status || 405,
          ));
        }
      },
    );

    module.exports = {
      sendNotification,
    };
    ```

1. В консоль напишите `node index.js`. Запустится сервер.
1. В отдельном окне терминала выполните тестовый запрос к вашему серверу:

    ```text translate=no
    curl -X POST -L 'http://localhost:8080/notification' -H 'Content-Type: application/json' -d '{"notificationType": "PING", "time": "2025-01-01T00:00:00.000Z"}'
    ```

1. В ответе вы увидите `{"name":"shop","time":"2025-02-28T12:32:01.918Z","version":"1.0.0"}`, а в логах сервера сообщение `PING notification processed`.
