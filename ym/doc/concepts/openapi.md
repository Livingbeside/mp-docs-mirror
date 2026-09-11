---
title: Спецификация OpenAPI
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/openapi.md"
fetched_at: "2026-09-11T01:57:18Z"
content_sha: aa3b245fa0150025
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.57.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/openapi.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/openapi.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/openapi.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/concepts/openapi.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Спецификация OpenAPI

Спецификация OpenAPI для запросов магазина к Маркет доступна [на GitHub](https://github.com/yandex-market/yandex-market-partner-api). Вы можете использовать ее для упрощения и ускорения разработки интеграции.

## Как сгенерировать клиент API Яндекс Маркета для продавцов {#how-to}

Спецификация поможет сгенерировать файлы клиента на любом языке или фреймворке, которые поддерживает OpenAPI-генератор. Это может значительно упростить интеграцию с Яндекс Маркетом через API.

### Получить спецификацию через git {#git}

Есть два способа:

1. Выполнить команду `git clone https://github.com/yandex-market/yandex-market-partner-api.git`
2. Скачать архив с репозиторием через GitHub web-ui: в правом верхнем углу нажмите зеленую кнопку `Code` и в выпадающем списке выберите `Download ZIP`.

### Установка OpenAPI-генератора через пакетные менеджеры {#package-managers}

Документация генератора: <https://openapi-generator.tech/docs/installation>

**Для npm (любая ОС)**
`npm install @openapitools/openapi-generator-cli -g`

**Для Homebrew (macOS)**
`brew install openapi-generator`

**Для Scoop (Windows)**
`scoop install openapi-generator-cli`

### Генерация клиента {#client-generation}

**Для npm (любая ОС)**

```no-highlight translate=no
npx @openapitools/openapi-generator-cli generate -i <path_to_openapi.yaml> -g <lang> -o <output_path>
```

**Для остальных пакетных менеджеров**

```no-highlight translate=no
openapi-generator generate -i <path_to_openapi.yaml> -g <lang> -o <output_path>
```

Значения частей запроса:

`<lang>` — параметр генератора для выбранного языка или фреймворка.

`<output_path>` — выходная директория, куда будет помещен сгенерированный код клиента.

`<path_to_openapi.yaml>` — путь к файлу openapi.yaml данной спецификации.

Примеры генераторов:

* go
* java
* javascript
* kotlin
* php
* python
* ruby

Полный список генераторов доступен по ссылке: <https://openapi-generator.tech/docs/generators>
