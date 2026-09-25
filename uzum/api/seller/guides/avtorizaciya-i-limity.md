---
title: Авторизация и лимиты запросов
api: uzum-seller
kind: guide
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
content_sha: 06ad62921d8684a3
---

# Авторизация и лимиты запросов

Базовый адрес: `https://api-seller.uzum.uz/api/seller-openapi/`

## Авторизация

- **TokenAuth** — заголовок `Authorization`. Токен авторизации без префикса Bearer

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
