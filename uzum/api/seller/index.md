---
title: Uzum market seller openapi — все методы
api: uzum-seller
spec_version: 1.0.0
operations: 38
source: "https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html"
content_sha: bc2fb70406b0b959
---

# Uzum market seller openapi

Версия спеки: `1.0.0` · методов: **38** · разделов справки: **8**

Источник: https://api-seller.uzum.uz/api/seller-openapi/swagger/swagger-ui/swagger-ui/index.html

| Метод | Путь | Раздел | Описание |
|---|---|---|---|
| `GET` | `/v1/fbs/invoice/dop/drop-off-points` | FBS Invoice | [Возвращаем доступные пункты приема подходящие по габаритным группам, у которых есть хотя бы один таймслот раньше чем самая ранняя дата "доставить до", с оставшейся емкостью больше чем кол-во заказов в списке](fbs-invoice/get-v1-fbs-invoice-dop-drop-off-points.md) |
| `GET` | `/v1/fbs/invoice/dop/time-slot` | FBS Invoice | [Возвращает доступные тайм-слоты от текущего времени до минимальной даты «доставить до» среди переданных заказов, где оставшаяся емкость >= количеству заказов в списке](fbs-invoice/get-v1-fbs-invoice-dop-time-slot.md) |
| `GET` | `/v1/fbs/invoice/{invoiceId}/closing-documents` | FBS Invoice | [Печать акта приемки](fbs-invoice/get-v1-fbs-invoice-invoiceid-closing-documents.md) |
| `GET` | `/v1/fbs/invoice/{invoiceId}/orders` | FBS Invoice | [Получить FBS заказы по идентификатору накладной](fbs-invoice/get-v1-fbs-invoice-invoiceid-orders.md) |
| `GET` | `/v1/fbs/invoice/{invoiceId}/print` | FBS Invoice | [Печать акта поставки](fbs-invoice/get-v1-fbs-invoice-invoiceid-print.md) |
| `GET` | `/v1/fbs/invoice/{invoiceId}` | FBS Invoice | [Получить накладную по идентифкатору](fbs-invoice/get-v1-fbs-invoice-invoiceid.md) |
| `GET` | `/v1/fbs/invoice` | FBS Invoice | [Получить все накладные для FBS заказа](fbs-invoice/get-v1-fbs-invoice.md) |
| `GET` | `/v1/fbs/order/return-reasons` | Работа с заказами FBS/DBS | [Получение причин возврата](rabota-s-zakazami-fbs-dbs/get-v1-fbs-order-return-reasons.md) |
| `GET` | `/v1/fbs/order/{orderId}/labels/print` | Работа с заказами FBS/DBS | [Получить этикетку для FBS заказа](rabota-s-zakazami-fbs-dbs/get-v1-fbs-order-orderid-labels-print.md) |
| `GET` | `/v1/fbs/order/{orderId}` | Работа с заказами FBS/DBS | [Получение информации о заказе](rabota-s-zakazami-fbs-dbs/get-v1-fbs-order-orderid.md) |
| `GET` | `/v1/finance/expenses` | Finance | [Получение списка расходов продавца.](finance/get-v1-finance-expenses.md) |
| `GET` | `/v1/finance/orders` | Finance | [Получение списка заказов.](finance/get-v1-finance-orders.md) |
| `GET` | `/v1/invoice` | FBO Invoice | [Получение списка накладных](fbo-invoice/get-v1-invoice.md) |
| `GET` | `/v1/product/barcodes/types` | Product | [Справочник размеров (типов) этикеток](product/get-v1-product-barcodes-types.md) |
| `GET` | `/v1/product/shop/{shopId}` | Product | [Получение SKU по ID магазина](product/get-v1-product-shop-shopid.md) |
| `GET` | `/v1/return` | Return Invoice | [Получение возвратов продавца](return-invoice/get-v1-return.md) |
| `GET` | `/v1/shop/{shopId}/invoice/products` | FBO Invoice | [Получение состава накладной](fbo-invoice/get-v1-shop-shopid-invoice-products.md) |
| `GET` | `/v1/shop/{shopId}/invoice` | FBO Invoice | [Получение накладных поставки по ID магазина](fbo-invoice/get-v1-shop-shopid-invoice.md) |
| `GET` | `/v1/shop/{shopId}/return/{returnId}` | Return Invoice | [Получение состава накладной возврата](return-invoice/get-v1-shop-shopid-return-returnid.md) |
| `GET` | `/v1/shop/{shopId}/return` | Return Invoice | [Получение накладных возврата](return-invoice/get-v1-shop-shopid-return.md) |
| `GET` | `/v1/shops` | Shop | [Получение списка собственных магазинов.](shop/get-v1-shops.md) |
| `GET` | `/v2/fbs/orders/count` | Работа с заказами FBS/DBS | [Получить количество заказов](rabota-s-zakazami-fbs-dbs/get-v2-fbs-orders-count.md) |
| `GET` | `/v2/fbs/orders` | Работа с заказами FBS/DBS | [Получение заказов продавца](rabota-s-zakazami-fbs-dbs/get-v2-fbs-orders.md) |
| `GET` | `/v2/fbs/sku/stocks` | Stocks | [Получение остатков по SKU (устарело)](stocks/get-v2-fbs-sku-stocks.md) |
| `GET` | `/v3/fbs/sku/stocks` | Stocks | [Получение остатков по SKU (постранично)](stocks/get-v3-fbs-sku-stocks.md) |
| `POST` | `/v1/dbs/order/{orderId}/completed` | Работа с заказами FBS/DBS | [Подтверждение выдачи DBS-заказа](rabota-s-zakazami-fbs-dbs/post-v1-dbs-order-orderid-completed.md) |
| `POST` | `/v1/dbs/order/{orderId}/delivering` | Работа с заказами FBS/DBS | [Передача DBS-заказа в доставку](rabota-s-zakazami-fbs-dbs/post-v1-dbs-order-orderid-delivering.md) |
| `POST` | `/v1/dbs/order/{orderId}/refund` | Работа с заказами FBS/DBS | [Создание возврата по DBS-заказу](rabota-s-zakazami-fbs-dbs/post-v1-dbs-order-orderid-refund.md) |
| `POST` | `/v1/fbs/invoice/dop/time-slot` | FBS Invoice | [Обновление пункта приема и таймслота](fbs-invoice/post-v1-fbs-invoice-dop-time-slot.md) |
| `POST` | `/v1/fbs/invoice/{invoiceId}/cancel` | FBS Invoice | [Отмена накладной](fbs-invoice/post-v1-fbs-invoice-invoiceid-cancel.md) |
| `POST` | `/v1/fbs/invoice/{invoiceId}/update-content` | FBS Invoice | [Изменение состава накладной](fbs-invoice/post-v1-fbs-invoice-invoiceid-update-content.md) |
| `POST` | `/v1/fbs/invoice` | FBS Invoice | [Создание накладной](fbs-invoice/post-v1-fbs-invoice.md) |
| `POST` | `/v1/fbs/order/{orderId}/cancel` | Работа с заказами FBS/DBS | [Отмена заказа](rabota-s-zakazami-fbs-dbs/post-v1-fbs-order-orderid-cancel.md) |
| `POST` | `/v1/fbs/order/{orderId}/confirm` | Работа с заказами FBS/DBS | [Подтверждение заказа](rabota-s-zakazami-fbs-dbs/post-v1-fbs-order-orderid-confirm.md) |
| `POST` | `/v1/fbs/order/{orderId}/identifier` | Работа с заказами FBS/DBS | [Привязка идентификаторов к товарам заказа](rabota-s-zakazami-fbs-dbs/post-v1-fbs-order-orderid-identifier.md) |
| `POST` | `/v1/product/shop/{shopId}/barcodes/print` | Product | [Печать этикеток SKU](product/post-v1-product-shop-shopid-barcodes-print.md) |
| `POST` | `/v1/product/{shopId}/sendPriceData` | Product | [Изменение цен SKU](product/post-v1-product-shopid-sendpricedata.md) |
| `POST` | `/v2/fbs/sku/stocks` | Stocks | [Обновление остатков по SKU](stocks/post-v2-fbs-sku-stocks.md) |
