---
title: Загрузить медиафайл{{ /content/v3/media/file }}
api: wb-work-with-products
method: POST
path: /content/v3/media/file
operation_id: post-content-v3-media-file
tags:
  - mediaFiles
spec_version: items
source: "https://dev.wildberries.ru/docs/openapi/work-with-products"
deprecated: false
content_sha: 5ecabb5b81c7b5f0
---

# Загрузить медиафайл{{ /content/v3/media/file }}

`POST /content/v3/media/file`

Описание метода Метод загружает и добавляет один медиафайл к карточке товара. Требования к изображениям: * максимум изображений для одной карточки товара — 30 * минимальное разрешение — 700x900 px * максимальный размер — 32 Мб * минимальное качество — 65% * форматы — JPG, PNG, BMP, GIF (статичные), WebP Требования к видео: * максимум одно видео для одной карточки товара * максимальный размер — 50 Мб * форматы — MOV, MP4 Лимит запросов на один аккаунт продавца для всех методов Медиафайлов : | Тип | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | --- | | Персональный | 1 мин | 100 запросов | 600 мс | 5 запросов | | Сервисный | 1 мин | 100 запросов | 600 мс | 5 запросов | | Базовый с секретом | 1 мин | 100 запросов | 600 мс | 5 запросов | | Базовый | 1 ч | 2 запроса | 30 мин | 1 запрос | В песочнице — максимум 1 запрос в секунду суммарно для всех методов Контента .

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `X-Nm-Id` | header | string | да | Артикул WB |
| `X-Photo-Number` | header | integer | да | Номер медиафайла на загрузку, начинается с `1`. При загрузке видео всегда указывайте `1`. Чтобы добавить изображение к уже загруженным, номер медиафайла должен быть больше количества уже загруженных медиафайлов. |

## Запрос

**Тело запроса** (`multipart/form-data`):

- `uploadfile` — string<binary>

## Ответы

**200** — Успешно

- `data` — object
- `error` — boolean. Флаг ошибки
- `errorText` — string. Описание ошибки
- `additionalErrors` — object. Дополнительные ошибки

**400** — Неправильный запрос

- `additionalErrors` — object. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**402** — Требуется платёж

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)

**403** — Доступ запрещён

- `additionalErrors` — object. Дополнительные ошибки
- `data` — object. Данные ошибки
- `error` — boolean. Флаг ошибки
- `errorText` — string. Текст ошибки

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
