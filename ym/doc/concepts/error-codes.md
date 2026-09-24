---
title: Типы ошибок и что с ними делать
marketplace: yandex-market
source: "https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md"
fetched_at: "2026-09-24T02:13:10Z"
content_sha: 595ba5c0e59b0f54
---

---
metadata:
  - name: generator
    content: Diplodoc Platform v5.61.1
alternate:
  - https://yandex.ru/dev/market/partner-api/doc/en/concepts/error-codes.md
  - https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md
  - https://yandex.ru/dev/market/partner-api/doc/zh/concepts/error-codes.md
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/concepts/error-codes.md
    type: text/markdown
    title: Markdown version
  - href: https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt
    rel: describedby
---
> **Documentation Index:** Fetch the complete configuration index at https://yandex.ru/dev/market/partner-api/doc/ru/llms.txt

# Типы ошибок и что с ними делать

Если запрос не удалось выполнить, Маркет возвращает в ответ параметр `errors`. Он содержит коды возникших ошибок (параметр `code`) и их краткие описания (параметр `message`).

Если ошибок с определенным кодом станет слишком много, вы получите уведомление об этом в кабинете продавца на Маркете.

## Что обозначают коды ошибок {#codes}

#|
||**Код**|**Название**|**Что случилось и что делать**||
||[400](#400)| `Bad Request` | Что-то не так в содержании запроса. Например, ошибка в формате JSON-данных или вы пытаетесь изменить статус отмененного или доставленного заказа.

Ориентируйтесь на описание ошибки, чтобы понять, что именно не так.||
||[401](#401)| `Unauthorized` | В запросе не указан (или указан, но не там) токен авторизации.||
||[403](#403)| `Forbidden` |
* Токен авторизации не сработал. **Для OAuth-токена:** скорее всего, у него истек срок годности или вы удалили из числа сотрудников человека, на которого был оформлен токен.
* Другая ошибка доступа.
||
||[404](#404)| `Not Found` |
* Запрашиваемый метод или ресурс не найден. Проверьте адреса запросов, по которым обращается система.
* Указанный параметр не найден. Например, кампания. Проверьте корректность передаваемых данных.
* Версия метода не найдена. Проверьте корректность используемой версии.
||
||[405](#405)| `Method Not Allowed` | На указанном ресурсе нет такого метода.

Проверьте адреса запросов, по которым обращается система.||
||[415](#415)| `Unsupported Media Type` | Запрашиваемый тип контента не поддерживается методом.

Проверьте корректность запроса.||
||[420](#420)| `Enhance Your Calm` | Лимит запросов превышен.

Убедитесь, что ваша система не отправляет ничего лишнего.||
||[423](#423)| `Locked` | Метод невозможно использовать для этого магазина.

Ориентируйтесь на описание ошибки, чтобы понять, что именно не так.||
||[499](#499)| `Client Closed Request` | Клиент закрыл соединение до окончания обработки запроса на стороне Маркета. Проверьте таймауты на стороне клиента и повторите запрос.||
||[500](#500)| `Internal Server Error` | Внутренняя ошибка Маркета.||
||[503](#503)| `Service Unavailable` | Сервер Маркета перегружен.||
|#

## Ошибки в содержании запросов (400) {#400}

### Ошибки, встречающиеся во всех методах {#common}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**'field' elements must be not null (rejected value: 'value')** | Элементы коллекции не должны быть `null`. | Удалите или замените элементы со значением `null`.| Встречается во всех методах. ||

||**'field' must be greater than 'value' (rejected value: 'value')** | Значение должно быть строго больше порога. | Укажите значение из допустимого диапазона.| Встречается во всех методах. ||

||**'field' must be greater than or equal to 'value' (rejected value: 'value')** | Значение должно быть больше либо равно порогу. | Укажите значение из допустимого диапазона.| Встречается во всех методах. ||

||**'field' must be less than or equal to 'value' (rejected value: 'value')** | Значение должно быть меньше либо равно порогу. | Укажите значение из допустимого диапазона.| Встречается во всех методах. ||

||**'field' must match 'regexp' (rejected value: 'value')** | Значение не соответствует требуемому шаблону. | Передайте значение, соответствующее регулярному выражению.| Встречается во всех методах. ||

||**'field' must not be empty (rejected value: 'value')** | Поле не должно быть пустым. | Передайте непустое значение поля.| Встречается во всех методах. ||

||**'field' must not be null (rejected value: null)** | Обязательное поле не передано. | Укажите значение поля.| Встречается во всех методах. ||

||**'field' size must be between 'min' and 'max' (rejected size: 'size')** | Недопустимый размер коллекции: должен быть от 'min' до 'max'. | Измените количество элементов до допустимого.| Встречается во всех методах. ||

||**'field' size must be between 'min' and 'max' (rejected value: 'value')** | Недопустимая длина значения: должна быть от 'min' до 'max'. | Передайте значение допустимой длины.| Встречается во всех методах. ||

||**Campaign type is not allowed. Allowed campaign types: 'campaignTypes'** | Метод не поддерживает модель работы вашего магазина. | Убедитесь, что вы используете метод, который поддерживает модель работы вашего магазина.| Встречается во всех методах. ||

||**Content type 'contentType' not supported** | Запрашиваемый тип контента не поддерживается. | Передайте один из поддерживаемых типов контента в заголовке `Content-Type`. [Подробнее о формате входных данных](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/input-format.md) | Встречается во всех методах. ||

||**Illegal input at 'path'** | Недопустимое значение по указанному пути. | Проверьте структуру и типы в теле запроса по указанному пути; исправьте названия полей и форматы значений, чтобы соответствовать ожидаемой схеме JSON. Если тип контента не JSON, укажите корректный `Content-Type`. | Встречается во всех методах. ||

||**JSON: {message}** | В формате JSON-данных содержится ошибка. | Проверьте корректность JSON. | Встречается во всех методах. ||

||**Required request body is missing** | Требуется тело запроса, но оно не передано. | Убедитесь, что передали тело запроса для метода, где оно обязательно. | Встречается во всех методах. ||

||**Required request parameter 'param' is not present** | Обязательный для передачи параметр не передан. | Убедитесь, что передали все обязательные для используемого метода входные параметры. | Встречается во всех методах. ||

||**The request is too big: Maximum allowed request size must be less than 'maxSize' KB, but passed 'size' MB** | Запрос слишком большой: размер переданного запроса больше максимально допустимого. | Уменьшите тело запроса; при большом объёме разбейте данные на несколько меньших запросов, чтобы каждый не превышал лимит. | Встречается во всех методах. ||

||**The request is too big: {message}** | Превышено ограничение на размер HTTP-запроса. | Размер содержимого не может превышать 512 КБ. Разбейте запрос на несколько.| Встречается во всех методах. ||

||**Type mismatch: 'value'** | Тип входного значения не совпадает с ожидаемым типом параметра. | Передавайте значения в корректном формате и типе, которые можно посмотреть на странице соответствующих методов. | Встречается во всех методах. ||

||**Unexpected end of content** | Тело запроса неожиданно завершается. | Проверьте корректность формата данных, передаваемых в теле запроса.| Встречается во всех методах. ||

||**Incorrect X-Business-Id header value: 'value'** | Некорректное значение заголовка `X-Business-Id`. | Передайте корректное положительное числовое значение идентификатора кабинета в заголовке `X-Business-Id`. | Встречается во всех методах. ||

||**URL businessId ('urlBusinessId') does not match businessId in X-Business-Id header ('headerBusinessId')** | Идентификатор кабинета в URL не совпадает с идентификатором в заголовке `X-Business-Id`. | Убедитесь, что `businessId` в URL совпадает со значением в заголовке `X-Business-Id`. | Встречается во всех методах, в которых `businessId` передается в URL. ||
|#

### Ошибки пагинации {#pagination}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Bad page token**| Некорректный токен пагинации.| Проверьте корректность передаваемого токена пагинации. [Подробнее про пагинацию в запросах](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/pagination.md). | Встречается во всех методах, где используется пагинация. ||

||**Parameter limit must be less than or equal to 'max-limit' (rejected value: 'limit')**| Превышено ограничение на количество значений на одной странице — параметр `limit`.| Уменьшите количество значений. | Встречается во всех методах, где используется пагинация. ||

|#

### Ошибки при работе с заказами {#orders}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Action is not allowed for order 'orderId' with status 'status' and substatus 'substatus'** | Действие недоступно для заказа в текущем статусе и подстатусе. | Подробную инструкцию по работе с заказами для вашего типа размещения можно посмотреть в разделе [Пошаговые инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/index.md). | [POST v2/campaigns/{campaignId}/orders/{orderId}/delivery/track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) ||

||**Attempt to change order items or instances after READY_TO_SHIP** | Попытка изменить позиции заказа или коды маркировки после перехода в статус `READY_TO_SHIP`. | Не пытайтесь изменить состав заказа или коды маркировки после перехода в статус `READY_TO_SHIP`. Подробную инструкцию по работе с заказами для вашего типа размещения можно посмотреть в разделе [Пошаговые инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/index.md). | [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) ||

||**Can't create return for order with status: 'status'**|Нельзя создать возврат для заказа в текущем статусе.|Создавайте возврат только для заказа в статусе `DELIVERED`.|[POST v1/campaigns/{campaignId}/returns/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md) ||

||**Can't resolve geo for address 'address'**|Передан некорректный адрес доставки.|Проверьте корректность адреса доставки: укажите полный адрес, включая регион и населенный пункт.|[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md) ||

||**Cancellation request substatus 'subbstatus' is not available for status 'status' and role 'role' for order 'orderId'** | Подстатус запроса на отмену недоступен для указанного сочетания статуса и роли. | Используйте корректный подстатус с учетом статуса заказа и вашей роли. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**Cannot do operation for order with status 'status', and substatus 'substatus' (partnerId = 'partnerId', orderId = 'orderId')** | Невозможно выполнить операцию для заказа в текущем статусе и подстатусе. | Не передавайте внешний идентификатор после перехода заказа в статус `PROCESSING` с подстатусом `READY_TO_SHIP`. | [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md) ||

||**Cannot do operation, external ID already set for order (partnerId = 'partnerId', orderId = 'orderId', externalId = 'externalId')** | Нельзя выполнить операцию: внешний идентификатор уже передан для заказа. | Не пытайтесь передавать внешний идентификатор заказа больше одного раза. | [POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md) ||

||**Delivery date <date> can't be in the future** | Дата доставки не может быть в будущем. | Установите дату доставки не позднее текущего момента. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**Delivery dates can't be updated for 'deliveryType' order with id 'orderId'**|Нельзя изменить даты доставки для указанного типа доставки.|Проверьте тип доставки заказа и меняйте дату только для курьерской доставки.|[POST v1/campaigns/{campaignId}/orders/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md) ||

||**Exceeded the number of days to edit delivery dates! limit is: 'days' days** | Превышен допустимый период для редактирования дат доставки. | Переносите дату не дальше, чем на указанный лимит дней. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md) ||

||**Exceeded the number of edits of delivery dates! limit is: 'limit'** | Превышено количество изменений дат доставки. | — | [PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md) ||

||**Failed to upload photos**|Не удалось обработать ссылки на фотографии.|Проверьте, что ссылки на фото валидны и доступны, или используйте другой хостинг.|[POST v1/campaigns/{campaignId}/returns/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md) ||

||**Invalid filters: interval between 'dateFrom' and 'dateTo' is more than 'range' days.** | Неверные фильтры: интервал между начальной и конечной датами превышает допустимое значение. | Уменьшите период до допустимого предела или разделите запрос на несколько меньших интервалов. | [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) ||

||**Invalid incoming cis for item with id = %d for reason: {reason}** | Передан некорректный код маркировки для товара в заказе. | Проверьте, что передаваемый код маркировки (`cis`) непустой и имеет корректный формат. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) ||

||**Invalid order boxes layout request. Violations: {violations}** | Некорректный запрос раскладки коробок. | Исправьте раскладку согласно списку нарушений и повторите запрос. Проверьте, что не указываете один и тот же товар, как разные объекты в одной коробке; одна коробка не содержит и товары целиком, и части товаров. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) ||

||**Invalid status for order 'orderId': 'status', PROCESSING expected** | Недопустимый статус заказа, ожидается статус `PROCESSING`. | Используйте метод только для цифровых заказов в статусе `PROCESSING`. Подробнее про работу с цифровыми заказами можно почитать в [пошаговой инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/digital.md). | [POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md) ||

||**Merchant return with id: 'returnId' already exists**|Возврат с таким внешним идентификатором уже существует.|Передавайте уникальный `externalReturnId` для нового возврата.|[POST v1/campaigns/{campaignId}/returns/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md) ||

||**New delivery dates are the same as the current!** | Новая дата доставки совпадает с текущей. | Передайте измененную дату доставки. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md) ||

||**No permission to set status 'newStatus' for order 'orderId' with status 'currentStatus'** | Не разрешено установить переданный статус для заказа с текущим статусом. | Убедитесь, что пытаетесь перевести заказ в корректный статус. Подробную инструкцию по работе с заказами для вашего типа размещения можно посмотреть в разделе [Пошаговые инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/index.md). | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**No transition found: 'fromStatus' -> 'toStatus'** | Не найден переход между статусами. | Передайте корректный статус для изменения статуса заказа. Подробную инструкцию по работе с заказами для вашего типа размещения можно посмотреть в разделе [Пошаговые инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/index.md). | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**Not a business buyer.** | Покупатель — не юридическое лицо. | Воспользуйтесь методом получения информации о покупателе — физическом лице [GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md). | [POST v2/campaigns/{campaignId}/orders/{orderId}/business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md) ||

||**Not enough stock for items: 'offerIds'**|Товара недостаточно в наличии.|Передавайте только товары с нужным количеством остатка.|[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md) ||

||**Offers not found for SKUs: 'offerIds'**|Переданы несуществующие идентификаторы товаров.|Проверьте корректность `offerIds`.|[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md)
[POST v1/campaigns/{campaignId}/returns/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md)
[POST v1/campaigns/{campaignId}/delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getDeliveryOptions.md)
[POST v1/campaigns/{campaignId}/return-delivery-options](https://yandex.ru/dev/market/partner-api/doc/ru/reference/delivery-options/getReturnDeliveryOptions.md) ||

||**Order 'orderId' is in cancellation state**|Заказ находится в процессе отмены.|Не изменяйте отменённый заказ.|[POST v1/campaigns/{campaignId}/orders/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md) ||

||**Order 'orderId' is in terminal state**|Нельзя изменить заказ в финальном статусе.|Не изменяйте заказ в статусах `DELIVERED` или `CANCELLED`.|[POST v1/campaigns/{campaignId}/orders/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md) ||

||**Order already exists with external id 'externalOrderId'**|Заказ с таким внешним идентификатором уже существует.|Передавайте уникальный `externalOrderId` для нового заказа.|[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md) ||

||**Order creation start date is required to be less than end date** | Начальная дата для фильтрации заказов по дате оформления должна быть меньше конечной. | Установите начало периода строго раньше конца; при необходимости поменяйте местами даты или скорректируйте одну из них. | [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) ||

||**Order is in the wrong status, it’s only possible starting from the status PROCESSING.** | Заказ в неподходящем статусе; операция возможна только со статуса PROCESSING. | Убедитесь, что передаваемый заказ находится в статусе `PROCESSING`, `DELIVERY`, `PICKUP` или `DELIVERED`. | [POST v2/campaigns/{campaignId}/orders/{orderId}/business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md) ||

||**Order is not in shop-processing status (actual: 'status').** | Заказ не находится в статусе обработки магазином. | Получить данные можно, только если заказ находится в статусе `PROCESSING`, `DELIVERY` или `PICKUP`. | [GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md) ||

||**Order shipment start date is required to be less than end date** | Начальная дата для фильтрации заказов по дате отгрузки в службу доставки должна быть меньше конечной. | Установите начало периода строго раньше конца; при необходимости поменяйте местами даты или скорректируйте одну из них. | [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) ||

||**Order update start is required to be less than end date** | Начальная дата для фильтрации заказов по дате и времени обновления должна быть меньше конечной. | Установите начало периода строго раньше конца; при необходимости поменяйте местами даты или скорректируйте одну из них. | [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md) ||

||**Order.id='orderId' is not digital.** | Передаваемый заказ не цифровой. | Убедитесь, что переданный заказ - цифровой. Метод доступен только для работы с цифровыми заказами. | [POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md) ||

||**Real delivery date should be from order creation date to current date inclusively** | Фактическая дата доставки должна быть от даты создания заказа до текущей даты включительно. | Укажите фактическую дату доставки в диапазоне от даты создания заказа до текущей даты включительно. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**Status change was forbidden for client role = 'role'** | Изменение статуса заказа запрещено для роли клиента. | — | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**Status not allowed: 'status'** | Перевод заказа в передаваемый статус не допускается. | Проверьте корректность передаваемого статуса заказа. Допускается перевод заказа в статусы `PROCESSING`, `CANCELLED`, `DELIVERY`, `PICKUP`, `DELIVERED`.| [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**String (value) is not a valid country code according to ISO 3166-1 alpha-2** | Недопустимый код страны. | Укажите код страны в формате ISO 3166-1 alpha-2. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) ||

||**The requested delivery interval is not valid for order 'orderId'**|Передан некорректный интервал дат доставки.|Проверьте доступные интервалы доставки и передайте актуальный интервал.|[POST v1/campaigns/{campaignId}/orders/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/createOrder.md)
[POST v1/campaigns/{campaignId}/orders/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrder.md) ||

||**Transition 'fromStatus' -> 'toStatus' is not allowed. Reason: {reason}** | Смена статуса заказа из текущего в целевой недоступна. | Убедитесь, что пытаетесь перевести заказ в корректный статус. Подробную инструкцию по работе с заказами для вашего типа размещения можно посмотреть в разделе [Пошаговые инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/step-by-step/index.md).| [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) ||

||**Wrong count for shop skus: 'offerIds'**|Передано некорректное количество товаров в возврате.|Проверьте, что количество товаров в возврате не превышает количество товаров в заказе.|[POST v1/campaigns/{campaignId}/returns/create](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/createReturn.md) ||
|#

### Ошибки при работе с отгрузками (FBS) {#shipments}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Closest shipment for reception transfer act generation not found.** | Отгрузки в статусе **Можно обрабатывать** не найдены. | Создайте заявку на поставку или дождитесь перехода существующей заявки в нужный статус. | [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md) ||

||**Cutoff time for shipments has not been reached yet** | Время подтверждения отгрузки еще не наступило. | Дождитесь начала времени подтверждения отгрузки по графику склада и повторите попытку. Проверить возможность подтверждения отгрузки можно с помощью метода [GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md): среди доступных действий `availableActions` должно быть действие `CONFIRM`. | [POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md) ||

||**No orders for closest shipment have been processed yet (shipmentId: 'shipmentId').** | Нет заказов в ближайшей отгрузке. | Проверьте, что у заказов параметр `status` имеет значение `PROCESSING`, а параметр `substatus` — `READY_TO_SHIP`. Получить статусы и даты отгрузки заказов можно с помощью метода [POST v1/businesses/{businessId}/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getBusinessOrders.md), изменить статусы заказов — с помощью методов [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) и [POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md). | [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md) ||

||**Outbound with id = 'shipmentId' is not confirmed and hasn't draft transfer** | Отгрузка не подтверждена. | Прежде чем получить акт приема-передачи, необходимо подтвердить отгрузку. Для этого воспользуйтесь методом  [POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md). | [GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentAct.md) ||

||**Shipment with ID 'shipmentId' contains invalid orders. Reasons: orders are in wrong status ('orderIds')** | Отгрузка содержит заказы в неверных статусах. | Для подтверждения в отгрузке должны быть только заказы в допустимых статусах: `PROCESSING` с подстатусом `READY_TO_SHIP` или `SHIPPED`, либо `DELIVERY`, `DELIVERED`, `PICKUP`. Переведите некорректные заказы в разрешённые статусы или перенесите их в следующую отгрузку с помощью метода [POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/orders/transfer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/transferOrdersFromShipment.md) и повторите подтверждение. | [POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md) ||

||**Shipment with ID 'shipmentId' does not contain any orders** | В отгрузке нет ни одного заказа. | Добавьте заказы в отгрузку: переведите их в допустимые статусы. Затем повторите подтверждение. | [POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md) ||

||**Shipment with ID 'shipmentId' has been confirmed already** | Отгрузка уже подтверждена. | Не повторяйте подтверждение отгрузки. Чтобы получить акт приема-передачи для подтвержденной отгрузки используйте метод [GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentAct.md). | [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)
[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md) ||

||**Some orders are in the process of being excluded from shipment (shipmentId: 'shipmentId', orderIds: 'orderIds'). Please wait up to 30 minutes and try again.** | Идентификаторы заказов в ближайшей отгрузке, которые в процессе удаления из нее. | Перенос заказов может занимать до 30 минут. Дождитесь окончания переноса и попробуйте снова. | [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md) ||

||**Some orders have not been processed yet. Please change the status of orders to READY_TO_SHIP and try again. (shipmentId: 'shipmentId', orderIds: 'orderIds').** | Идентификаторы заказов в ближайшей отгрузке, которые еще не обработаны. | Передайте для заказов с указанными идентификаторами `status: PROCESSING` и `substatus: READY_TO_SHIP` и попробуйте еще раз. Изменить статусы заказов можно с помощью запросов [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md) и [POST v2/campaigns/{campaignId}/orders/status-update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatuses.md). | [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md) ||
|#

### Ошибки при работе с ценами {#prices}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**discountBase is less than value: offerId = 'offerId'** | Зачеркнутая цена меньше текущей цены товара. | Установите зачеркнутую цену не ниже текущей. Если скидки нет — не указывайте зачеркнутую цену. | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) ||

||**Duplicate offer in request: offerId = 'offerId'** | Дублирующийся товар в запросе. | Проверьте уникальность передаваемых товаров. | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) ||

||**Missing offerId** | Отсутствует идентификатор товара. | Передайте непустой `offerId`. | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) ||

||**Missing price value: offerId = 'offerId'** | Отсутствует значение цены товара. | Передавайте значение цены товара. | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) ||

||**Offer at index 'index' should have valid discount value. Discount percentage must be between 'min' and 'max', actual 'val'** | У товара указано недопустимое значение скидки: процент скидки должен быть от 'min' до 'max'. | Укажите процент скидки в допустимом диапазоне.| [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
[POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)||

||**Offer at index 'index' should not have 'fieldName' with 'currency' currency** | Для цены указана неверная валюта. | Передайте цену в валюте кабинета. Валюту в кабинете можно посмотреть с помощью метода [GET v2/campaigns/{campaignId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/campaigns/getCampaignSettings.md). | [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
[POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md) ||

||**Offer at index 'index' should not have 'fieldName' with too many digits** | Для поля передано слишком много знаков после запятой. | Передайте значение с не более чем 7 знаками после запятой. | [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
[POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md) ||

||**offerId = 'offerId' should have valid discount value. Discount percentage must be between min' and 'max', actual 'val'** | У товара указано недопустимое значение скидки: процент скидки должен быть от 'min' до 'max'. | Укажите процент скидки в допустимом диапазоне.| [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) ||

||**Unrecognized vat: 'value': offerId = 'offerId'** | Нераспознанная ставка НДС. | Передайте корректную ставку НДС для товара. Посмотреть допустимые идентификаторы НДС можно на странице метода [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md). | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) ||

||**Vat setting of 'vatName' ('vatId') not supported for current 'taxSystemName' ('taxSystemId') taxSystem: 'offerId'** | Ставка НДС не поддерживается для текущей системы налогообложения. | Используйте поддерживаемую ставку НДС для вашей налоговой системы/страны. | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)
[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md) ||

||**Vat setting of 'vatName' ('vatId') not supported since year 2019: 'offerId'** | Ставка НДС не поддерживается с 2019 года. | Не используйте неподдерживаемую ставку 18%. Укажите актуальную поддерживаемую ставку для вашей налоговой системы/страны. | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)
[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md) ||
|#

### Ошибки при работе с товарами {#offers}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Duplicate offerId='offerId' at positions 'positions'** | Переданы дублирующиеся товары. | Обеспечьте уникальность товаров в передаваемом списке. | [POST v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/addHiddenOffers.md) ||

||**Offer at index 'index' cannot have parameter 'fieldName' deleted and set at the same time** | Можно передать либо значение параметра в `deleteParameters`, либо соответствующий параметр в `UpdateOfferDTO`. | Чтобы удалить ранее переданный параметр, укажите его значение в `deleteParameters` и не передавайте в `UpdateOfferDTO`.<br><br>Если хотите установить новое значение параметра, передайте его в `UpdateOfferDTO` и не указывайте в `deleteParameters`. | [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md) ||

||**Offer at index 'index' should not have empty values in list of 'fieldName'** | Товар не должен содержать пустые значения в списке. | Удалите пустые элементы из списка 'fieldName' или замените их валидными значениями. | [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md) ||

||**Offer at index 'index' should have weightDimensions.<weightDimension> greater than 0** | Габариты упаковки и вес товара должны быть положительными. | Передайте положительные значения для габаритов упаковки и веса товара. | [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md) ||

||**Offers should have different ids. Following offers ids are repeating: 'offerIds'.** | Передаваемые товары должны быть уникальными. | Проверьте уникальность передаваемых идентификаторов товаров. | [POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md) ||
|#

### Ошибки при работе с остатками {#stocks}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Duplicate shop-sku 'sku' for warehouse 'count'** | Дублирующийся shop-sku для склада. | Проверьте уникальность передаваемых значений `sku`.| [PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)
[POST v3/businesses/{businessId}/offers/stocks/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md) ||

||**Stock for 'sku' should not be in the future** | Данные об остатках для товара не должны быть в будущем. | Установите `updatedAt` не позднее текущего момента. | [PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)
[POST v3/businesses/{businessId}/offers/stocks/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md) ||

||**Stock for 'sku' should not be older than a day** | Данные об остатках для товара не должны быть старше суток. | Передайте актуальную дату и время обновления (не старше 24 часов) в поле `updatedAt`. | [PUT v2/campaigns/{campaignId}/offers/stocks](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocks.md)
[POST v3/businesses/{businessId}/offers/stocks/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/stocks/updateStocksOnPartnerWarehouses.md) ||
|#

### Ошибки при работе с точками продаж {#outlets}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**datediff-is-to-big-local** | При доставке по своему региону разница между максимальным и минимальным сроком доставки не должна превышать двух дней. | Убедитесь, что разница между `maxDeliveryDays` и `minDeliveryDays` не превышает двух дней. | [POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md) ||

||**datediff-is-to-big-long-period** | При доставке в другие регионы, где минимальный срок доставки больше 18 дней, разница между максимальным и минимальным сроком доставки не должна превышать минимальный срок. | Убедитесь, что разница между `maxDeliveryDays` и `minDeliveryDays` не превышает `minDeliveryDays`. | [POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md) ||

||**datediff-is-to-big-remote** | При доставке в другие регионы разница между максимальным и минимальным сроком доставки не должна превышать четырех дней. | Убедитесь, что разница между `maxDeliveryDays` и `minDeliveryDays` не превышает четырех дней. | [POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md) ||

||**Not valid outlet info: 'errors'** | Недопустимые данные точки продаж. | Исправьте данные точки продаж согласно тексту ошибки (адрес, регион, часы работы, обязательные поля, формат значений и т. п.) и повторите запрос. Полные требования к полям смотрите в описаниях соответствующих методов. | [POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md) ||

||**Outlet with code 'shopOutletCode' already exists for campaign 'campaignId'** | Точка продаж с переданным идентификатором `shopOutletCode` уже существует. | Значение идентификатора `shopOutletCode` должно быть уникальным в рамках одной кампании. | [POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md) ||

||**Region 'regionName' cannot be used as outlet region** | Регион не может использоваться в качестве адреса точки продаж. | Указывайте только регионы типов `TOWN` (город), `CITY` (крупный город) и `REPUBLIC_AREA` (район субъекта федерации). Тип региона указан в выходном параметре `type` запросов [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md) и [GET v2/regions/{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md). | [POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md) ||

||**Wrong outlet gps coordinates** | Неверные GPS‑координаты точки продаж. | Укажите координаты в формате: долгота, широта. Разделители: запятая и/или пробел. Например, `20.4522144, 54.7104264`. | [POST v2/campaigns/{campaignId}/outlets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/createOutlet.md)
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md) ||
|#

### Ошибки при работе с категориями {#categories}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Category is not a leaf.** | Категория не является листовой. | Используйте идентификатор листовой категории (категория, у которой нет дочерних). Чтобы получить дерево категорий на Маркете, воспользуйтесь методом [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md). | [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md) ||

||**Following categories are not leaf categories: 'categories'** | Переданные категории не являются листовыми. | Используйте идентификаторы листовых категорий (категории, у которой нет дочерних). Чтобы получить дерево категорий на Маркете, воспользуйтесь методом [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md). | [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md) ||

||**Unknown categories: 'categories'** | Переданы неизвестные категории. | Проверьте корректность передаваемых идентификаторов категорий.
Чтобы узнать идентификатор категории, к которой относится интересующий вас товар, воспользуйтесь запросом [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md). | [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md) ||

||**Requested businessId ('requestedBusinessId') does not match businessId in X-Business-Id header ('headerBusinessId')** | Идентификатор кабинета в query-параметре не совпадает с идентификатором в заголовке `X-Business-Id`. | Убедитесь, что `businessId` в query-параметре совпадает со значением в заголовке `X-Business-Id`. | [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md) ||
|#

### Ошибки при работе с тарифами {#tariffs}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Invalid parameter: payout frequency 'frequency' and delay weeks 'paymentDelayWeeks' are not supported** | Передана неподдерживаемая комбинация частоты и отсрочки выплат. | Для кабинета в РФ поддерживаются: частота `DAILY`; либо частота `WEEKLY` с отсрочкой выплат 1, 2 или 4 недели (`paymentDelayWeeks`). | [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md) ||

||**Currency 'currency' is not supported for tariff calculation** | Передана валюта, неподдерживаемая для расчёта тарифов. | Укажите валюту из поддерживаемых для расчёта тарифов. | [POST v2/tariffs/calculate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/tariffs/calculateTariffs.md) ||
|#

### Ошибки при работе с акциями {#promos}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Not enough parameters in request: offerIds or deleteAllOffers should be specified** | Не передан параметр для удаления товаров из акции. | Чтобы убрать все товары, передайте значение `true` в параметре `deleteAllOffers`. Чтобы удалить только некоторые товары, передайте их SKU в параметре `offerIds`. | [POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md) ||

||**Promo has ended** | Акция закончилась. | Проверьте корректность передаваемого идентификатора акции. Чтобы узнать, в каких акциях можно поучаствовать, воспользуйтесь методом [POST v2/businesses/{businessId}/promos](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromos.md). | [POST v2/businesses/{businessId}/promos/offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/getPromoOffers.md)
[POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md)
[POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md) ||

||**The limit for promo update requests with a single offerId has been exceeded. Please wait or use batch requests with multiple offerIds for the same promoId.** | Превышен лимит запросов на обновление акции для одного товара в запросе. | Подождите и повторите попытку позже, либо используйте запросы с несколькими товарами в списке `offers` для одной и той же акции. | [POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md)
[POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md) ||

||**Too many parameters in request: only one of parameters offerIds or deleteAllOffers should be specified** | Можно либо передать значение `true` в параметре `deleteAllOffers`, либо SKU товаров в параметре `offerIds`. | Передайте что-то одно  — или значение `true` в параметре `deleteAllOffers`, или SKU товаров в параметре `offerIds`. | [POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md) ||
|#

### Ошибки в отчетах и документах {#reports}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Contract with type MARKETING was signed with the agency** | Договор на маркетинг заключен с агентством. | Для получения информации по закрывающим документам обратитесь к своему агентству. | [POST v2/reports/closure-documents/detalization/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateClosureDocumentsDetalizationReport.md)||

||**Date field 'dateFieldTo' must be greater or equal to 'dateFieldFrom'!** | Дата окончания интервала должна быть не меньше даты начала. | Установите конец периода не раньше начала; при необходимости скорректируйте даты или поменяйте их местами. | [POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md) ||

||**Only default prices are used for this business. Generate the report at the business level (not campaign) to see actual prices.** | Для этого кабинета используются только единые цены кабинета. | Сформируйте отчет на уровне бизнеса (не кампании). Проверить, включены ли магазинные цены можно с помощью параметра `onlyDefaultPrice` в методе [POST v2/businesses/{businessId}/settings](https://yandex.ru/dev/market/partner-api/doc/ru/reference/businesses/getBusinessSettings.md). | [POST v2/reports/goods-prices/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/generateGoodsPricesReport.md) ||

||**Periods "orderDate" and "orderUpdate" can't be specified simultaneously!** | Нельзя одновременно указывать периоды по дате формирования заказа и по дате изменения. | Укажите только один период: либо по дате формирования, либо по дате изменения. | [POST v2/campaigns/{campaignId}/stats/orders](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders-stats/getOrdersStats.md) ||

||**Without subscription, you cannot request data older than 90 days. The dateFrom ('dateFrom') is too far in the past.** | Без подписки нельзя запрашивать данные старше 90 дней. | Оформите подписку для доступа к данным за более длительный период, либо укажите `dateFrom` не ранее чем 90 дней от текущей даты. Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription). | Встречается в методах генерации отчетов. ||

||**You cannot request data older than 400 days. The dateFrom ('dateFrom') is too far in the past.** | Нельзя запрашивать данные старше 400 дней. | Укажите `dateFrom` не ранее чем 400 дней от текущей даты. | Встречается в методах генерации отчетов. ||
|#

### Ошибки при работе с отзывами о товарах {#feedback}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Duplicate comment.** | Уже есть комментарий с таким текстом. | Не передавайте комментарий, совпадающий с уже существующим. | [POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md) ||

||**Illegal url in comment text.** | В тексте комментария найдены ссылки на сторонние ресурсы. | Удалите ссылки и при необходимости добавьте те, которые ведут на Маркет. | [POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md) ||
|#

### Ошибки при работе с вопросами о товарах {#questions}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается** ||

||**parentEntityId required for CREATE operation** | Для создания необходим ID вопроса или ответа как родительской сущности. | Укажите в запросе `parentEntityId`. | [POST v1/businesses/{businessId}/goods-questions/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md) ||

||**entityId required for UPDATE and DELETE operation** | Для обновления и удаления необходим ID обновляемого ответа или комментария. | Укажите в запросе `entityId`. | [POST v1/businesses/{businessId}/goods-questions/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md) ||

||**QUESTION entity type cannot be updated** | Вопрос нельзя изменить после создания.|Измените тип сущности на ответ или комментарий. | [POST v1/businesses/{businessId}/goods-questions/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md) ||

||**Cannot create a comment on another comment.** | Нельзя создать комментарий к комментарию.|Измените тип родительской сущности на ответ. | [POST v1/businesses/{businessId}/goods-questions/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-questions/updateGoodsQuestionTextEntity.md) ||
|#
## Ошибки 401 Unauthorized {#401}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Api-Key token is invalid** | Api-Key-токен недействителен. | Проверьте написание Api-Key-токена. Если ошибка сохраняется, получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Встречается во всех методах. ||

||**Api-Key token is not specified** | В запросе не указан Api-Key-токен. | Передавайте Api-Key-токен в заголовке `Api-Key` по [инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md#use). | Встречается во всех методах. ||

||**Api-Key token length invalid** | Неправильная длина Api-Key-токена. | Проверьте написание Api-Key-токена. Если ошибка сохраняется, получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Встречается во всех методах. ||

||**Api-Key token prefix invalid** | Неправильный префикс Api-Key-токена. | Убедитесь, что в заголовке вы не используете префикс `Bearer`. [Как передавать Api-Key-токен](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md#use)

Если префикса нет, проверьте написание Api-Key-токена. Если ошибка сохраняется, получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Встречается во всех методах. ||

||**Api-Key token format invalid** | Неправильный формат Api-Key-токена. | Проверьте написание Api-Key-токена. Если ошибка сохраняется, получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Встречается во всех методах. ||

||**Api-Key token is revoked** | Api-Key-токен был удален. | Получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Встречается во всех методах. ||

||**Authorization header has invalid syntax** | Формат HTTP-заголовка `Authorization` некорректен. | Сделайте заголовок по [инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md#use). | Встречается во всех методах. ||

||**Credentials are not specified** | В запросе не указаны авторизационные данные. | Сделайте заголовок по инструкции:

* [Api-Key-токен](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md#use)
* [OAuth-токен](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md#use) | Встречается во всех методах. ||

||**OAuth client id is not specified** | В запросе не указан идентификатор клиента OAuth (`client_id`). | Укажите `client_id` вашего приложения в заголовке `oauth_client_id`. | Встречается во всех методах. ||

||**OAuth credentials are not specified** | В запросе не указаны авторизационные данные. | Сделайте заголовок `Authorization` по [инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md#use). | Встречается во всех методах. ||

||**OAuth token is not specified** | В запросе не указан авторизационный OAuth-токен. | Сделайте заголовок `Authorization` по [инструкции](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md#use). | Встречается во всех методах. ||
|#

## Ошибки 403 Forbidden {#403}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Access denied** | Доступ запрещен. | Проверьте правильность указания ресурса, а также наличие прав доступа к нему у пользователя, чей токен авторизации используется в запросе. [Подробно о доступе](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md) | Встречается во всех методах. ||

||**The method is deprecated and is occasionally forbidden. Please stop using it** | Метод устарел, и часть запросов к нему отклоняется. Не используйте его. | Перейдите на актуальный метод, указанный в документации. Ошибка возвращается интеграциям, продолжающим вызывать устаревший метод; доля таких ответов со временем увеличивается. | Встречается во всех методах. ||

||**API for business 'businessId' disabled because it has only disabled partners** | API кабинета отключено, потому что все его магазины отключены. | Включите API хотя бы для одного магазина в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any/api-settings). Если включение невозможно, исправьте причины отключения магазинов. [Подробная инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md#business-disabled) | Встречается во всех методах. ||

||**API for campaign 'campaignId' disabled because it has no placement program** | API магазина отключено, потому что у него нет программы размещения. | Завершите подключение магазина к программе размещения в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any). [Подробная инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md#no-placement-program) | Встречается во всех методах. ||

||**API for campaign 'campaignId' disabled because there are no active contracts with Market** | API магазина отключено из-за отсутствия активного договора с Маркетом. | Завершите подключение кабинета в разделе [«Юридические данные»](https://partner.market.yandex.ru/business/any) в кабинете продавца на Маркете. [Подробная инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md#no-contract) | Встречается во всех методах. ||

||**API for campaign 'campaignId' disabled due to inactivity** | API магазина отключено из-за неактивности — на витрине долго не было товаров. | Чтобы возобновить работу через API, включите интеграцию в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any/api-settings) и проверьте, корректно ли она работает. [Подробная инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md#inactivity) | Встречается во всех методах. ||

||**API for campaign 'campaignId' manually disabled** | Вы выключили интеграцию — все запросы к Маркету отклоняются. | Включите интеграцию в [кабинете продавца на Маркете](https://partner.market.yandex.ru/business/any/api-settings). [Подробная инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-access.md#manually-disabled) | Встречается во всех методах. ||

||**Client id is invalid** | Указан некорректный идентификатор клиента OAuth (`client_id`). | Укажите `oauth_client_id` того же приложения, которым выпущен токен, или перевыпустите токен нужным клиентом. | Встречается во всех методах. ||

||**Contact not found for login 'login' and campaignId 'campaignId'** | Не найдена учетная запись пользователя, логин которой передан для подписи электронного акта приема-передачи. | Выберите логин пользователя, который привязан к кабинету или магазину. | Встречается во всех методах. ||

||**Contacts with available roles for signing not found for login 'login'** | Учетная запись пользователя, логин которой передан для подписи электронного акта приема-передачи, не обладает необходимыми доступами. | Передайте логин пользователя, который привязан к кабинету или магазину и обладает необходимыми доступами. [Доступы к методам по Api-Key](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/access.md) | Встречается во всех методах. ||

||**Electronic signature is only available for API token authorization.** | Электронная подпись доступна только при авторизации по Api-Key. | Выполните запрос с авторизацией по Api-Key. Как передавать Api-Key: [инструкция](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md#use). | [GET v2/campaigns/{campaignId}/shipments/reception-transfer-act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentReceptionTransferAct.md)\
[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md) ||

||**No access to campaigns: 'campaigns'** | Нет доступа к указанным магазинам. | Передавайте только кампании, принадлежащие указанному кабинету (`businessId`). | Встречается во всех методах. ||

||**No access to comment modifying.** | Нет доступа к изменению указанного комментария. | Проверьте корректность передаваемого идентификатора комментария. | [POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md) ||

||**No access to feedback modifying.** | Нет доступа к изменению указанного отзыва. | Проверьте корректность передаваемого идентификатора отзыва. | [POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md) ||

||**OAuth token is invalid** | Указанный авторизационный OAuth-токен недействителен. | Получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md) | Встречается во всех методах. ||

||**OAuth token is invalid (account has been globally logged out)**|Пользователь воспользовался функцией [«Выйти везде»](https://yandex.ru/dev/id/doc/ru/tokens/token-invalidate) в Яндекс ID.|Получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Встречается во всех методах. ||

||**Scope is invalid** | OAuth-токен получен через приложение без доступа к Маркету. | Получите новый токен. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/oauth-2.0.md) | Встречается во всех методах. ||

||**The method is not supported for Market Yandex Go sellers** | Метод недоступен для продавцов Market Yandex Go.

Эти ограничения указаны в описании к методам. | — | Встречается во всех методах. ||

||**The partner does not have access to the supply request.** | У партнёра нет доступа к заявке на поставку. | Проверьте корректность передаваемого идентификатора заявки. | [POST v2/campaigns/{campaignId}/supply-requests/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md)
[POST v2/campaigns/{campaignId}/supply-requests/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestItems.md)||

||**Token does not have any of the scopes to access the API method** | Нет доступа к методу. | Получите доступ хотя бы к одной группе методов, которые перечислены в тексте ошибки. [Как это сделать](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/api-key.md) | Встречается во всех методах. ||

||**User account is disabled** | Учетная запись пользователя, для которого выдан указанный токен авторизации, заблокирована. | Обратитесь в службу поддержки. | Встречается во всех методах. ||

||**businessId in X-Business-Id header ('headerBusinessId') does not match the business that the campaign 'campaignId' belongs to ('actualBusinessId')** | Идентификатор кабинета в заголовке `X-Business-Id` не совпадает с кабинетом, к которому принадлежит магазин. | Убедитесь, что в заголовке `X-Business-Id` указан идентификатор кабинета, к которому принадлежит переданный идентификатор магазина. | Встречается во всех методах, в которых передается `campaignId`. ||

||**Entity id from request body does not match businessId in X-Business-Id header ('businessId')** | Идентификатор сущности в теле запроса (`businessId`/`campaignId`) не совпадает с идентификатором кабинета в заголовке `X-Business-Id`. | Если в теле запроса передан `businessId`, то убедитесь, что он совпадает со значением в заголовке `X-Business-Id`. Если передан `campaignId`, то убедитесь, что магазин относится к бизнесу, переданному в заголовке `X-Business-Id`. | Встречается в методах генерации отчетов. ||
|#

## Ошибки 404 Not Found {#404}

#|
||**Report not found.** | Указанный в запросе отчет или документ не найден. | Проверьте корректность передаваемого идентификатора отчета или документа. | [GET v2/reports/info/{reportId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/reports/getReportInfo.md) ||

||**Resource not found** | Ресурс не найден. |
* Проверьте точность URL и HTTP‑метода, их можно посмотреть в документации на странице метода.
* Убедитесь, что используете корректную версию метода.

[Подробнее о вызове методов](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/method-call.md) | Встречается во всех методах. ||

||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Box not found. Box: 'boxId'** | Указанная в запросе коробка не найдена. | Проверьте корректность передаваемого идентификатора коробки. | [GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md) ||

||**Campaign not found 'campaignId'** | Указанная в запросе кампания не найдена. | Проверьте корректность передаваемого идентификатора кампании. | Встречается во всех кабинетных методах. ||

||**Campaign 'campaignId' has no order id 'orderId'** | Указанный заказ не принадлежит магазину. | Проверьте, что идентификатор заказа указан для магазина, переданного в запросе. | [POST v2/campaigns/{campaignId}/orders/{orderId}/delivery/track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md) ||

||**Can't find chat by id: 'chatId'** | Указанный в запросе чат не найден. | Проверьте корректность передаваемого идентификатора чата. | [GET v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatMessage.md)\
[POST v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/sendMessageToChat.md)\
[POST v2/businesses/{businessId}/chats/history](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatHistory.md) ||

||**Can't find message by id: 'messageId' for chat 'chatId'** | Указанное в запросе сообщение в переданном чате не найдено. | Проверьте корректность передаваемых идентификаторов сообщения и чата. | [GET v2/businesses/{businessId}/chats/message](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/getChatMessage.md) ||

||**Failed to find &#91;'resource'&#93; with id &#91;'id'&#93;** | Указанный в запросе ресурс не найден. | Проверьте корректность передаваемого идентификатора ресурса (заказа или отгрузки). | [GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipment.md)
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/act](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentAct.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/delivery/track](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryTrackCode.md)
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/orders/info](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/getShipmentOrdersInfo.md)
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/transportation-waybill](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentTransportationWaybill.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/verifyEac](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/verifyOrderEac.md)\
[PUT v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallets](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/setShipmentPalletsCount.md)\
[GET v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/pallet/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/downloadShipmentPalletLabels.md)\
[POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/orders/transfer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/transferOrdersFromShipment.md) ||

||**Failed to find order with id 'orderId'** | Указанный в запросе заказ не найден. | Проверьте корректность передаваемого идентификатора заказа. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md) ||

||**Feedbacks not found.** | Указанные в запросе отзывы не найдены. | Проверьте корректность передаваемых идентификаторов отзывов. | [POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md) ||

||**Grade not found.** | Отзыв не найден. | Проверьте корректность передаваемого идентификатора отзыва. | [POST v2/businesses/{businessId}/goods-feedback/comments/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/goods-feedback/updateGoodsFeedbackComment.md) ||

||**No boxes found for order 'orderId'** | Для указанного в запросе заказа не найдены коробки. | Проверьте корректность передаваемого идентификатора заказа.
Убедитесь, что передали информацию о том, как товары распределены по коробкам. Для этого воспользуйтесь методом [PUT v2/campaigns/{campaignId}/orders/{orderId}/boxes](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/setOrderBoxLayout.md). | [GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels/data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md) ||

||**Order not found: 'orderId'** | Указанный в запросе заказ не найден. | Проверьте корректность передаваемого идентификатора заказа. | [PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/storage-limit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/updateOrderStorageLimit.md)
[POST v2/businesses/{businessId}/chats/new](https://yandex.ru/dev/market/partner-api/doc/ru/reference/chats/createChat.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md) ||

||**Order not found: partnerId = 'partnerId', orderId = 'orderId'** | Указанный в запросе заказ не найден. | Проверьте корректность передаваемого идентификатора заказа. | [GET v2/campaigns/{campaignId}/orders/{orderId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrder.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateOrderStatus.md)
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/shipments/{shipmentId}/boxes/{boxId}/label](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabel.md)
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/generateOrderLabels.md)
[GET v2/campaigns/{campaignId}/orders/{orderId}/delivery/labels/data](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-labels/getOrderLabelsData.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/deliverDigitalGoods](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderDigitalCodes.md)
[GET v2/campaigns/{campaignId}/orders/{orderId}/buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/getOrderBuyerInfo.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/cancellation/accept](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/acceptOrderCancellation.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/delivery/date](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-delivery/setOrderDeliveryDate.md)
[PUT v2/campaigns/{campaignId}/orders/{orderId}/identifiers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/provideOrderItemIdentifiers.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/business-buyer](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessBuyerInfo.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/order-business-information/getOrderBusinessDocumentsInfo.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/external-id](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/updateExternalOrderId.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/identifiers/status](https://yandex.ru/dev/market/partner-api/doc/ru/reference/orders/getOrderIdentifiersStatus.md) ||

||**Outlet not found: 'outletId'** | Указанная в запросе точка продаж не найдена. | Проверьте корректность передаваемого идентификатора точки продаж. | [GET v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/getOutlet.md)
[DELETE v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/deleteOutlet.md)
[PUT v2/campaigns/{campaignId}/outlets/{outletId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/outlets/updateOutlet.md) ||

||**Region 'regionId' not found.** | Указанный в запросе регион не найден. | Проверьте корректность передаваемого идентификатора региона.
Для получения списка всех доступных регионов используйте справочный метод [GET v2/regions](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsByName.md) | [GET v2/regions/{regionId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionsById.md)\
[GET v2/regions/{regionId}/children](https://yandex.ru/dev/market/partner-api/doc/ru/reference/regions/searchRegionChildren.md) ||

||**Return 'returnId' for order 'orderId' is not found** | Указанный в запросе возврат не найден. | Проверьте корректность передаваемых идентификаторов возврата и заказа. | [GET v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/getReturn.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/setReturnDecision.md)
[POST v2/campaigns/{campaignId}/orders/{orderId}/returns/{returnId}/decision/submit](https://yandex.ru/dev/market/partner-api/doc/ru/reference/returns/submitReturnDecision.md) ||

||**Shipment with ID 'shipmentId' not found** | Указанная в запросе отгрузка не найдена. | Проверьте корректность передаваемого идентификатора отгрузки. | [POST v2/campaigns/{campaignId}/first-mile/shipments/{shipmentId}/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/shipments/confirmShipment.md) ||

||**Supply request not found.** | Заявка не найдена. | Проверьте корректность передаваемого идентификатора заявки. | [POST v2/campaigns/{campaignId}/supply-requests/documents](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestDocuments.md)
[POST v2/campaigns/{campaignId}/supply-requests/items](https://yandex.ru/dev/market/partner-api/doc/ru/reference/supply-requests/getSupplyRequestItems.md) ||

||**Unknown category** | Неизвестная категория. | Проверьте корректность передаваемого идентификатора категории.
Чтобы узнать идентификатор категории, к которой относится интересующий вас товар, воспользуйтесь запросом [POST v2/categories/tree](https://yandex.ru/dev/market/partner-api/doc/ru/reference/categories/getCategoriesTree.md). | [POST v2/category/{categoryId}/parameters](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/getCategoryContentParameters.md) ||
|#

## Ошибки 405 Method Not Allowed {#405}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Request method 'method' not supported** | Запрашиваемый HTTP-метод не поддерживается. | Проверьте методы, которые поддерживаются ресурсом. | Встречается во всех методах. ||
|#

## Ошибки 415 Unsupported Media Type {#415}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Content type 'content-type' not supported** | Запрашиваемый тип контента не поддерживается. | Передайте один из поддерживаемых типов контента. | Встречается во всех методах. ||

||**Unknown content-type: 'content-type'** | Запрашиваемый тип контента — неизвестен. | Передайте один из поддерживаемых типов контента. | Встречается во всех методах. ||
|#

## Ошибки 420 Enhance Your Calm {#420}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Hit rate limit of 'N' parallel requests for {entity}** | Превышено глобальное ограничение на количество одновременных запросов к API Яндекс Маркета. [Что это такое](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/limits.md#global) | Уменьшите количество параллельных запросов к API для конкретной сущности до `N` запросов. | Встречается во всех методах. ||

||**Hit rate limit of 'N' requests per 'period' for resource 'R' for {entity}** | Превышено ресурсное ограничение на количество `N` запросов к ресурсу `R` за период `period` для конкретной сущности. [Что это такое](https://yandex.ru/dev/market/partner-api/doc/ru/concepts/limits.md#resource)| Время, до которого действует ограничение, указано в заголовке `X-RateLimit-Resource-Until`. Использование ресурса станет возможным после наступления указанного времени. | Встречается во всех методах. ||

||**Active reports limit exceeded, limit='limit'** | Превышен лимит на количество одновременно генерируемых отчетов. | Дождитесь завершения генерации предыдущих отчетов, прежде чем создавать новые. Количество одновременно генерируемых отчетов зависит от вашего тарифного плана. Подробнее о подписке для продавцов читайте [в Справке Маркета для продавцов](https://yandex.ru/support/marketplace/ru/marketing/subscription). | Встречается в методах генерации отчетов. ||
|#
## Ошибки 423 Locked {#423}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Business is in migration** | В кабинете происходят миграции магазинов. | Дождитесь окончания переноса. | [POST v2/businesses/{businessId}/offer-cards/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/content/updateOfferContent.md)
[POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md)
[POST v2/businesses/{businessId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updateBusinessPrices.md)
[POST v2/businesses/{businessId}/price-quarantine/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmBusinessPrices.md)
[POST v2/campaigns/{campaignId}/price-quarantine/confirm](https://yandex.ru/dev/market/partner-api/doc/ru/reference/price-quarantine/confirmCampaignPrices.md)
[POST v2/campaigns/{campaignId}/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/updateCampaignOffers.md)
[POST v2/campaigns/{campaignId}/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/offers/deleteCampaignOffers.md)
[POST v2/businesses/{businessId}/offer-mappings/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/updateOfferMappings.md)
[POST v2/businesses/{businessId}/offer-mappings/archive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/addOffersToArchive.md)
[POST v2/businesses/{businessId}/offer-mappings/unarchive](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffersFromArchive.md)
[POST v2/businesses/{businessId}/offer-mappings/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/deleteOffers.md)
[POST v1/businesses/{businessId}/offer-mappings/barcodes/generate](https://yandex.ru/dev/market/partner-api/doc/ru/reference/business-offer-mappings/generateOfferBarcodes.md)
[POST v2/businesses/{businessId}/promos/offers/update](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/updatePromoOffers.md)
[POST v2/businesses/{businessId}/promos/offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/promos/deletePromoOffers.md) ||

||**Campaign is in business migration** | Магазин находится в процессе переноса в другой кабинет. | Дождитесь окончания переноса. | [GET v2/campaigns/{campaignId}/hidden-offers](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/getHiddenOffers.md)
[POST v2/campaigns/{campaignId}/hidden-offers/delete](https://yandex.ru/dev/market/partner-api/doc/ru/reference/hidden-offers/deleteHiddenOffers.md) ||

||**Partner use only default price** | В кабинете используются цены для всех магазинов. | Установить цену для отдельного магазина не получится. Задавайте единые цены для всех магазинов кабинета. | [POST v2/campaigns/{campaignId}/offer-prices/updates](https://yandex.ru/dev/market/partner-api/doc/ru/reference/prices/updatePrices.md) ||
|#

## Ошибки 499 Client Closed Request {#499}

Ошибка возвращается, когда клиент закрывает соединение до завершения обработки запроса на стороне Маркета. Проверьте настройки таймаутов и политику повторов запросов на стороне клиента и повторите вызов.

## Ошибки 500 Internal Server Error {#500}

Подождите некоторое время и вызовите метод повторно. Если проблема не решится, обратитесь в службу поддержки — перейдите в [кабинет продавца на Маркете](https://partner.market.yandex.ru/business/any/support) и нажмите кнопку **Создать обращение**.

## Ошибки 503 Service Unavailable {#503}

#|
||**Описание**|**Перевод**|**Что делать**|**Методы, в которых ошибка встречается**||

||**Service temporarily unavailable. Please, try again later** | Сервер временно недоступен из-за высокой загрузки. | Попробуйте повторить запрос через некоторое время.

Если проблема не решится, обратитесь в службу поддержки — перейдите в [кабинет продавца на Маркете](https://partner.market.yandex.ru/business/any/support) и нажмите кнопку **Создать обращение**. | Встречается во всех методах. ||
|#

## Пример сообщения об ошибке {#example}

Запрос:

```httpget translate=no
GET v2/campaigns/10003/orders HTTP/1.1
Host: api.partner.market.yandex.ru
Accept: */*
Api-Key: ACMA:I4c4CxCSYaI41RSC2uYWP2qj3Rhhm4knMiBEga5K:151c0664a
```

Ответ:

```json translate=no
{
  "errors": [
    {
      "code": "UNAUTHORIZED",
      "message": "Api-Key token is invalid"
    }
  ],
  "status": "ERROR"
}
```
