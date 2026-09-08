---
title: Информация о медиакампании
api: wb-promotion
method: GET
path: /adv/v1/advert
operation_id: getV1Advert
tags:
  - media
spec_version: promotion
source: "https://dev.wildberries.ru/docs/openapi/promotion"
deprecated: false
content_sha: a4e75d2635cede3a
---

# Информация о медиакампании

`GET /adv/v1/advert`

Описание метода

Метод возвращает информацию о кампании [WB Медиа](https://cmp.wildberries.ru/cmpf/list). Вместо карточек товаров в медиакампаниях продвигаются рекламные баннеры продавца на сайте и в приложении WB.

Лимит запросов на один аккаунт продавца:

| Тип | Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- | --- |
| Персональный | 1 сек | 10 запросов | 100 мс | 10 запросов |
| Сервисный | 1 сек | 10 запросов | 100 мс | 10 запросов |
| Базовый с секретом | 1 сек | 10 запросов | 100 мс | 10 запросов |
| Базовый | 1 ч | 5 запросов | 12 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `id` | query | integer | да | ID медиакампании |

## Ответы

**200** — Успешно

- `advertId` — integer. ID медиакампании
- `name` — string. Название медиакампании
- `brand` — string. Название бренда
- `type` — integer. Тип медиакампании: - `1` — размещение по дням - `2` — размещение по просмотрам
- `status` — integer. Статус медиакампании: - `1` — черновик - `2` — модерация - `3` — отклонена (с возможностью вернуть на модерацию) - `4` — готова к запуску - `5` — запланирована - `6` — на показах - `7` — завершена - `8` — отменена - `9` — приостановлена продавцом - `10` — пауза по дневному лимиту - `11` — пауза
- `createTime` — string<date-time>. Время создания медиакампании
- `extended` — object
  - `reason` — string. Комментарий модератора
  - `expenses` — integer. Затраты
  - `from` — string<date-time>. Дата и время начала показа медиакампании
  - `to` — string<date-time>. Дата и время окончания показа медиакампании
  - `updated_at` — string<date-time>. Дата и время изменения кампании
  - `price` — integer. Стоимость размещения по дням для типа `1`
  - `budget` — integer. Остаток бюджета для типа `2`
  - `operation` — integer. Источник списания: - `1` — баланс - `2` — счёт
  - `contract_id` — integer. ID контракта, для продавцов на контракте
- `items` — array[object]. Информация о баннере. Наличие в ответе тех или иных полей зависит от конфигурации медиакампании.
  - `id` — integer. ID баннера
  - `name` — string. Бренд
  - `status` — integer. Статус (такой же как у медиакампании)
  - `place` — integer. Позиция на странице размещения
  - `budget` — integer. Бюджет
  - `daily_limit` — integer. Дневной лимит (для баннеров по показам)
  - `category_name` — string. Название категории размещения
  - `cpm` — integer. Ставка
  - `url` — string. URL страницы, на которую попадает пользователь при клике по баннеру
  - `advert_type` — integer. Тип продвижения: - `1` — баннер - `2` — всплывающее меню - `3` — почтовая рассылка - `4` — социальные сети - `5` — push-уведомления в мобильном приложении
  - `created_at` — string<date-time>. Дата создания баннера
  - `updated_at` — string<date-time>. Дата и время обновления баннера
  - `date_from` — string<date-time>. Дата начала работы баннера
  - `date_to` — string<date-time>. Дата завершения работы баннера
  - `nms` — array[integer]. Подборка артикулов WB
  - `bottomText1` — string. Текст под плашкой баннера
  - `bottomText2` — string. 2-я строка с текстом под плашкой баннера
  - `message` — string. Текст push-уведомления или рассылки
  - `additionalSettings` — integer. Дополнительные настройки. Формат почтовой рассылки: - `1` — общий - `2` — частичный - `3` — уникальный Социальная сеть: - `1` — VK - `2` — OK (Одноклассники)
  - `receiversCount` — integer. Кол-во получателей push-уведомлений
  - `subject_id` — integer. ID родительской категории товара
  - `subject_name` — string. Название родительской категории товара
  - `action_name` — string. Название акции
  - `show_hours` — array[object]. Часы показа
    - `From` — integer. Начало показа
    - `To` — integer. Конец показа
  - `Erid` — string. Уникальный ID медиакампании для работы с ОРД

**204** — Медиакампания не найдена

**400** — Неправильный запрос

**401** — Не авторизован

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**403** — Доступ запрещён

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса

**429** — Слишком много запросов

- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `code` — string. Внутренний код ошибки
- `requestId` — string. Уникальный ID запроса
- `origin` — string. ID внутреннего сервиса WB
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
