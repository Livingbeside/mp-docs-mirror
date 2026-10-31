---
title: Авторизация и лимиты запросов
api: uzum-seller
kind: guide
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
content_sha: cbbb9a5a4fce5467
---

# Авторизация и лимиты запросов

Базовый адрес: `https://api-seller.uzum.uz/api/seller-openapi/`

## Авторизация

- **TokenAuth** — заголовок `Authorization`. Обязательный заголовок Authorization. Вставьте только значение API-ключа из личного кабинета продавца, без префикса Bearer. Swagger UI добавит заголовок автоматически. Заголовок token не используется.

## Лимиты запросов

Текущий лимит сообщают заголовки ответа:

| Заголовок | Что значит |
|---|---|
| `X-RateLimit-Remaining` | Оставшееся количество запросов на ближайшую секунду |
| `X-RateLimit-Replenish-Rate` | Скорость пополнения лимита запросов |
| `X-RateLimit-Burst-Capacity` | Максимальное количество запросов, которые могут быть выполнены за одну секунду |
| `X-RateLimit-Requested-Tokens` | Количество токенов, запрашиваемых за текущий запрос |
| `X-RateLimit-Limit-Per-Day` | Лимит запросов в день |
| `X-RateLimit-Remaining-Per-Day` | Оставшееся количество запросов в день |
