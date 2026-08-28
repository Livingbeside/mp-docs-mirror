---
title: Тестовые заказы
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md"
fetched_at: "2026-08-28T11:51:21Z"
content_sha: 6fbb2643ff3af4ea
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.55.3
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/sandbox.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/sandbox.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/sandbox.md
  - href: ru/concepts/sandbox.md
    type: text/markdown
    title: Markdown version
  - href: ../llms.txt
    type: text/markdown
    title: llms.txt
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Тестовые заказы

На Маркете есть возможность проверить работу магазина и его API на тестовых заказах, прежде чем начать работать с настоящими. Вы можете эмулировать процессы:

* оформление заказа от имени покупателя — добавлять товары в корзину, выбирать способы оплаты и условия доставки;
* отмена заказа.

Маркет не начисляет плату за такие заказы. А ошибки в работе с ними не влияют на проверки и не используются в расчете индекса качества.

Чтобы перейти в интерфейс отладки, в кабинете продавца на Маркете нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули** → **Тестовый заказ**.

Все созданные в интерфейсе отладки заказы поступают магазину со значением `true` параметра `fake`, что позволяет магазину отличать такие заказы от настоящих.

{% note warning "Данные по тестовым заказам" %}

Если у вас подключены API-уведомления, Маркет отправит вам запрос [POST notification](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/reference/sendNotification.md) с информацией о [событии](*notification-type) также и по тестовым заказам. [Как работать с уведомлениями](https://yandex.ru/dev/market/partner-api/doc/ru/push-notifications/index.md)

При этом методы, которые возвращают информацию по заказам, по умолчанию не включают данные по тестовым. Чтобы их получить, передайте значение `true` в параметре `fake`.

{% endnote %}

## Ограничения {#limitations}

Информация о тестовых заказах и логи запросов хранятся в течение 10 дней.

## Как провести отладку {#how-to}

### 1. Создайте новый заказ {#new-order}

На странице **API и модули** → **Тестовый заказ**:

1. Выберите **Создать в личном кабинете**.

2. Добавьте товары в корзину — нажмите ![](../_images/sandbox-button.png) рядом с нужными.

3. В блоке **Корзина** нажмите **Проверить наличие**.

![](../_images/concepts/sandbox-order.png)

### 2. Отправьте заказ {#accept}

В третьем блоке:

1. Укажите способ доставки и оплаты. Так как это тестовый заказ, выберите оплату при получении.

    {% note tip "Магазин создан только что" %}

    Настроенные службы доставки могут быть недоступны. В таком случае выберите тестовую службу.

    {% endnote %}

1. Введите тестовые данные покупателя (адрес, имя и фамилию, телефон и т. д.).

2. Нажмите **Отправить заказ**.

После этого на странице появится уведомление о создании нового заказа и его номер.

### 3. Обработайте заказ {#process}

{% note warning "После каждого запроса проверяйте лог" %}

Если интеграция настроена не совсем верно, вы увидите в логе ошибки, которые нужно исправить. Чтобы посмотреть лог, в кабинете продавца на Маркете нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули** → вкладка **Лог запросов**.

{% endnote %}

1. Отправьте запрос [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) c `orderIds` и сохраните идентификатор посылки (`id` в `shipments`) из ответа.

1. Отправьте запрос [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md), где передайте:

    * полученный идентификатор;
    * информацию о распределении товаров из заказа по коробкам;
    * если есть товары, которые подлежат маркировке, то коды маркировки для этих товаров.

1. Подтвердите готовность к отгрузке, передав статус `PROCESSING` с подстатусом `READY_TO_SHIP` с помощью запроса [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md).

1. Если в дальнейшем вы будете отгружать заказы в сортировочный центр или пункт приема или передавать их курьерам Маркета с вашего склада, отправьте запрос [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md). Передайте в нем статус `PROCESSING` с подстатусом `SHIPPED`.

### 4. Отмените заказ {#cancel}

Отправьте запрос [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) и передайте статус `CANCELLED` с причиной отмены `SHOP_FAILED`. Тестовый заказ можно отменить только до перевода в статус `PROCESSING` с подстатусом:

* `SHIPPED`, если в дальнейшем вы будете отгружать заказы в сортировочный центр или пункт приема или передавать их курьерам Маркета с вашего склада;

* `READY_TO_SHIP`, если ваш магазин подключен к экспресс‑доставке и вы будете отгружать заказы курьерам [Яндекс Go](https://go.yandex/).


Проверьте ошибки — в кабинете продавца на Маркете нажмите на иконку вашего аккаунта → **Настройки** и в меню слева выберите **API и модули** → вкладка **Лог запросов** — и исправьте их.

[*notification-type]: События, по которым Маркет присылает уведомления:<ul><li>создание нового заказа;</li><li>изменение заказа;</li><li>изменение статуса заказа;</li><li>создание нового чата с покупателем;</li><li>добавление нового сообщения в чате;</li><li>начало спора;</li><li>завершение спора;</li><li>создание нового отзыва о товаре;</li><li>создание нового комментария к отзыву;</li><li>создание заявки на отмену заказа;</li><li>отмена заказа;</li><li>создание нового невыкупа или возврата;</li><li>изменение статуса невыкупа или возврата.</li></ul>
