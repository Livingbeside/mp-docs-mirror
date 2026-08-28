---
title: Детализации к отчётам реализации по ID отчётов{{ /api/finance/v1/sales-reports/detailed/{reportId} }}
api: wb-financial-reports-and-accounting
method: POST
path: /api/finance/v1/sales-reports/detailed/{reportId}
operation_id: postV1SalesReportsDetailedReportId
tags:
  - financialReports
spec_version: finances
source: "https://dev.wildberries.ru/docs/openapi/financial-reports-and-accounting"
deprecated: false
content_sha: b801a70e02898488
---

# Детализации к отчётам реализации по ID отчётов{{ /api/finance/v1/sales-reports/detailed/{reportId} }}

`POST /api/finance/v1/sales-reports/detailed/{reportId}`

Описание метода

 Метод доступен по
 Персональному токену, 
 Сервисному токену

Метод возвращает детализации к [отчётам реализации](https://seller.wildberries.ru/suppliers-mutual-settlements) по ID отчётов.

Данные доступны с 1 января 2025 года.

Лимит запросов на один аккаунт продавца:

| Период | Лимит | Интервал | Всплеск |
| --- | --- | --- | --- |
| 1 мин | 1 запрос | 1 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `reportId` | path | integer<int64> | да | ID отчёта. Для ежедневных отчётов вместо стандартной десериализации рекомендуем использовать нестандартные библиотеки с поддержкой [BigInt](https://www.npmjs.com/package/json-bigint) |

## Запрос

**Тело запроса** (`application/json`):

- `fields` — array[string]. Список полей, которые вернутся в ответе. Если параметр не указан, возвращаются все поля
- `limit` — integer. Количество строк в ответе По умолчанию: `100000`.
- `rrdId` — integer. ID строки ответа. Необходим для получения отчёта частями. Начинайте загрузку отчёта с `"rrdid":0`. В последующих запросах передавайте значение `rrdId` из последней строки предыдущего ответа. Повторяйте запрос, пока не получите ответ `204` По умолчанию: `0`.

## Ответы

**200** — Успешно

- `acquiringBank` — string **обязательный**. Наименование банка-эквайера
- `acquiringFee` — string **обязательный**. Компенсация платёжных услуг/Комиссия за интеграцию платёжных сервисов
- `acquiringPercent` — number **обязательный**. Размер компенсации платёжных услуг/Комиссии за интеграцию платёжных сервисов, %
- `additionalPayment` — string **обязательный**. Корректировка Вознаграждения Вайлдберриз (ВВ)
- `agencyVat` — number. Удержание Агентского НДС, %. Только для продавцов из Кыргызстана
- `articleSubstitution` — string **обязательный**. ID подменного артикула
- `b2bCustomerTin` — string **обязательный**. ИНН B2B-покупателя
- `bonusTypeName` — string. Виды логистики, штрафов и корректировок ВВ
- `brandName` — string **обязательный**. Бренд
- `cashbackAmount` — string **обязательный**. Сумма, удержанная за начисленные баллы программы лояльности
- `cashbackCommissionChange` — string **обязательный**. Стоимость участия в программе лояльности
- `cashbackDiscount` — string **обязательный**. Компенсация скидки по программе лояльности
- `commissionPercent` — number **обязательный**. Размер кВВ, %
- `country` — string **обязательный**. Страна продажи
- `createDate` — string<date> **обязательный**. Дата формирования отчёта
- `currency` — string **обязательный**. Валюта отчёта
- `dateFrom` — string<date> **обязательный**. Дата начала отчётного периода
- `dateTo` — string<date> **обязательный**. Дата конца отчётного периода
- `declarationNumber` — string **обязательный**. Номер таможенной декларации
- `deduction` — string **обязательный**. Удержания
- `deliveryAmount` — integer **обязательный**. Количество доставок
- `deliveryMethod` — string **обязательный**. Способ продажи и тип товара
- `deliveryService` — string **обязательный**. Услуги по доставке товара покупателю
- `dlvPrc` — number **обязательный**. Фиксированный коэффициент склада по поставке
- `docTypeName` — string **обязательный**. Тип документа
- `fixTariffDateFrom` — string<date> **обязательный**. Дата начала действия фиксации
- `fixTariffDateTo` — string<date> **обязательный**. Дата конца действия фиксации
- `forPay` — string **обязательный**. К перечислению продавцу за реализованный товар
- `giBoxTypeName` — string **обязательный**. Тип коробов
- `giId` — integer **обязательный**. ID поставки
- `installmentCofinancingAmount` — string **обязательный**. Скидка по программе софинансирования
- `isB2b` — boolean **обязательный**. Признак B2B-продажи
- `isKgvpV2` — number **обязательный**. Размер снижения кВВ из-за акции, %
- `kiz` — string. Код маркировки [Честного знака](https://честныйзнак.рф/)
- `kvw` — number **обязательный**. Итоговый кВВ без НДС, %
- `kvwBase` — number **обязательный**. Размер кВВ без НДС, % базовый
- `loyaltyDiscount` — number **обязательный**. Размер скидки лояльности от продавца, %
- `loyaltyId` — integer **обязательный**. ID скидки лояльности от продавца
- `nmId` — integer **обязательный**. Артикул WB
- `officeName` — string **обязательный**. Склад
- `orderDt` — string<date-time> **обязательный**. Дата и время заказа
- `orderId` — integer **обязательный**. ID сборочного задания
- `orderUid` — string **обязательный**. ID корзины заказа — транзакции. Заказы в одной корзине покупателя будут иметь одинаковый `orderUid`
- `paidAcceptance` — string **обязательный**. Операции на приёмке
- `paidStorage` — string **обязательный**. Хранение
- `paidWithSocialCertificate` — boolean **обязательный**. Оплата социальным сертификатом
- `paymentProcessing` — string **обязательный**. Тип платежа: компенсация платёжных услуг/Комиссия за интеграцию платёжных сервисов
- `paymentSchedule` — string **обязательный**. Разовое изменение срока перечисления денежных средств
- `penalty` — string **обязательный**. Общая сумма штрафов
- `ppvzOfficeId` — integer **обязательный**. ID офиса доставки
- `ppvzOfficeName` — string **обязательный**. Наименование офиса доставки
- `ppvzReward` — string **обязательный**. Возмещение за выдачу и возврат товаров на ПВЗ
- `ppvzSalesCommission` — string **обязательный**. Вознаграждение с продаж до вычета услуг поверенного, без НДС
- `ppvzSupplierInn` — string **обязательный**. ИНН партнёра
- `ppvzSupplierName` — string **обязательный**. Партнёр
- `productDiscountForReport` — number **обязательный**. Итоговая согласованная скидка, %
- `quantity` — integer **обязательный**. Количество
- `rebillLogisticCost` — string **обязательный**. Возмещение издержек по перевозке/по складским операциям с товаром
- `rebillLogisticOrg` — string. Организатор перевозки
- `reportId` — integer<int64> **обязательный**. ID отчёта
- `reportType` — integer (1, 2, 3) **обязательный**. Тип отчёта: - `1` — основной - `2` — по выкупам - `3` — по выкупам для Грузии
- `retailAmount` — string **обязательный**. Вайлдберриз реализовал Товар (Пр)
- `retailPrice` — string **обязательный**. Цена розничная
- `retailPriceWithDisc` — string **обязательный**. Цена розничная с учётом согласованной скидки
- `returnAmount` — integer **обязательный**. Количество возврата
- `rrDate` — string<date> **обязательный**. Дата операции
- `rrdId` — integer **обязательный**. ID строки
- `saleDt` — string<date-time> **обязательный**. Дата и время продажи
- `salePercent` — integer **обязательный**. Согласованный продуктовый дисконт, %
- `salePriceAffiliatedDiscountPrc` — number **обязательный**. Скидка по подменному артикулу, %
- `salePricePromocodeDiscountPrc` — number **обязательный**. Скидка за промокод, %
- `salePriceWholesaleDiscountPrc` — number **обязательный**. Оптовая скидка для бизнеса, %
- `sellerOperName` — string **обязательный**. Обоснование для оплаты
- `sellerPromo` — string **обязательный**. Промокод, %
- `sellerPromoDiscount` — number **обязательный**. Размер дополнительной скидки по собственной акции продавца, %
- `sellerPromoId` — integer **обязательный**. ID собственной акции продавца с дополнительной скидкой
- `shkId` — integer **обязательный**. Штрихкод
- `sku` — string **обязательный**. Баркод
- `spp` — number **обязательный**. Платформенные скидки, %
- `srid` — string **обязательный**. ID заказа. В ответах методов сборочных заданий [FBS](./orders-fbs#tag/Sborochnye-zadaniya-FBS), [DBW](./orders-dbw#tag/dbwAssemblyOrders), [DBS](./orders-dbs#tag/dbsAssemblyOrders) и [Самовывоз](./in-store-pickup#tag/inStorePickupAssemblyOrders) `srid` равен `rid`
- `srvDbs` — boolean **обязательный**. Признак услуги платной доставки
- `stickerId` — string **обязательный**. Стикер МП
- `subjectName` — string **обязательный**. Предмет
- `supRatingUp` — number **обязательный**. Размер снижения кВВ из-за рейтинга, %
- `techSize` — string **обязательный**. Размер
- `title` — string **обязательный**. Название товара
- `trbxId` — string **обязательный**. ID короба для обработки товара
- `uuidPromocode` — string **обязательный**. ID промокода
- `vendorCode` — string **обязательный**. Артикул продавца
- `vw` — string **обязательный**. Вознаграждение Вайлдберриз (ВВ), без НДС
- `vwNds` — string **обязательный**. НДС с вознаграждения Вайлдберриз
- `warehouseLogisticsCoeff` — number **обязательный**. Коэффициент логистики
- `wibesDiscountPercent` — number **обязательный**. Скидка Wibes, %

**204** — Нет данных

**400** — Неправильный запрос

- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — integer. HTTP статус-код
- `title` — string. Заголовок ошибки

**401** — Не авторизован

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**402** — Требуется платёж

- `detail` — string. Детали ошибки. Ошибка возвращается только сервисам из [Каталога решений для бизнеса](/business-solutions)
- `title` — string. Заголовок ошибки

**403** — Доступ запрещён

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки

**429** — Слишком много запросов

- `code` — string. Внутренний код ошибки
- `detail` — string. Детали ошибки
- `origin` — string. ID внутреннего сервиса WB
- `requestId` — string. Уникальный ID запроса
- `status` — number. HTTP статус-код
- `statusText` — string. Расшифровка HTTP статус-кода
- `timestamp` — string<date-time>. Дата и время запроса
- `title` — string. Заголовок ошибки
