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
content_sha: a7eecb6046b4ad96
---

# Детализации к отчётам реализации по ID отчётов{{ /api/finance/v1/sales-reports/detailed/{reportId} }}

`POST /api/finance/v1/sales-reports/detailed/{reportId}`

Описание метода Метод доступен по Персональному токену, Сервисному токену Метод возвращает детализации к [отчётам реализации](https://seller.wildberries.ru/suppliers-mutual-settlements) по ID отчётов. Данные доступны с 1 января 2025 года. Лимит запросов на один аккаунт продавца: | Период | Лимит | Интервал | Всплеск | | --- | --- | --- | --- | | 1 мин | 1 запрос | 1 мин | 1 запрос |

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `reportId` | path | integer<int64> | да | ID отчёта. Для ежедневных отчётов вместо стандартной десериализации рекомендуем использовать нестандартные библиотеки с поддержкой [BigInt](https://www.npmjs.com/package/json-bigint) |

## Запрос

**Тело запроса** (`application/json`):

- `limit` — integer. Количество строк в ответе По умолчанию: `100000`.
- `rrdId` — integer. ID строки ответа. Необходим для получения отчёта частями. Начинайте загрузку отчёта с `"rrdid":0`. В последующих запросах передавайте значение `rrdId` из последней строки предыдущего ответа. Повторяйте запрос, пока не получите ответ `204` По умолчанию: `0`.
- `fields` — array[string]. Список полей, которые вернутся в ответе. Если параметр не указан, возвращаются все поля

## Ответы

**200** — Успешно

- `reportId` — integer<int64> **обязательный**. ID отчёта
- `dateFrom` — string<date> **обязательный**. Дата начала отчётного периода
- `dateTo` — string<date> **обязательный**. Дата конца отчётного периода
- `createDate` — string<date> **обязательный**. Дата формирования отчёта
- `currency` — string **обязательный**. Валюта отчёта
- `reportType` — integer (1, 2, 3) **обязательный**. Тип отчёта: - `1` — основной - `2` — по выкупам - `3` — по выкупам для Грузии
- `rrdId` — integer **обязательный**. ID строки
- `giId` — integer **обязательный**. ID поставки
- `dlvPrc` — number **обязательный**. Фиксированный коэффициент склада по поставке
- `fixTariffDateFrom` — string<date> **обязательный**. Дата начала действия фиксации
- `fixTariffDateTo` — string<date> **обязательный**. Дата конца действия фиксации
- `subjectName` — string **обязательный**. Предмет
- `nmId` — integer **обязательный**. Артикул WB
- `brandName` — string **обязательный**. Бренд
- `vendorCode` — string **обязательный**. Артикул продавца
- `title` — string **обязательный**. Название товара
- `techSize` — string **обязательный**. Размер
- `sku` — string **обязательный**. Баркод
- `docTypeName` — string **обязательный**. Тип документа
- `quantity` — integer **обязательный**. Количество
- `retailPrice` — string **обязательный**. Цена розничная
- `retailAmount` — string **обязательный**. Вайлдберриз реализовал Товар (Пр)
- `salePercent` — integer **обязательный**. Согласованный продуктовый дисконт, %
- `commissionPercent` — number **обязательный**. Размер кВВ, %
- `officeName` — string **обязательный**. Склад
- `sellerOperName` — string **обязательный**. Обоснование для оплаты
- `orderDt` — string<date-time> **обязательный**. Дата и время заказа
- `saleDt` — string<date-time> **обязательный**. Дата и время продажи
- `rrDate` — string<date> **обязательный**. Дата операции
- `shkId` — integer **обязательный**. Штрихкод
- `retailPriceWithDisc` — string **обязательный**. Цена розничная с учётом согласованной скидки
- `deliveryAmount` — integer **обязательный**. Количество доставок
- `returnAmount` — integer **обязательный**. Количество возврата
- `deliveryService` — string **обязательный**. Услуги по доставке товара покупателю
- `giBoxTypeName` — string **обязательный**. Тип коробов
- `productDiscountForReport` — number **обязательный**. Итоговая согласованная скидка, %
- `sellerPromo` — string **обязательный**. Промокод, %
- `spp` — number **обязательный**. Платформенные скидки, %
- `kvwBase` — number **обязательный**. Размер кВВ без НДС, % базовый
- `kvw` — number **обязательный**. Итоговый кВВ без НДС, %
- `supRatingUp` — number **обязательный**. Размер снижения кВВ из-за рейтинга, %
- `isKgvpV2` — number **обязательный**. Размер снижения кВВ из-за акции, %
- `ppvzSalesCommission` — string **обязательный**. Вознаграждение с продаж до вычета услуг поверенного, без НДС
- `forPay` — string **обязательный**. К перечислению продавцу за реализованный товар
- `ppvzReward` — string **обязательный**. Возмещение за выдачу и возврат товаров на ПВЗ
- `acquiringFee` — string **обязательный**. Компенсация платёжных услуг/Комиссия за интеграцию платёжных сервисов
- `acquiringPercent` — number **обязательный**. Размер компенсации платёжных услуг/Комиссии за интеграцию платёжных сервисов, %
- `paymentProcessing` — string **обязательный**. Тип платежа: компенсация платёжных услуг/Комиссия за интеграцию платёжных сервисов
- `acquiringBank` — string **обязательный**. Наименование банка-эквайера
- `vw` — string **обязательный**. Вознаграждение Вайлдберриз (ВВ), без НДС
- `vwNds` — string **обязательный**. НДС с вознаграждения Вайлдберриз
- `ppvzOfficeName` — string **обязательный**. Наименование офиса доставки
- `ppvzOfficeId` — integer **обязательный**. ID офиса доставки
- `ppvzSupplierName` — string **обязательный**. Партнёр
- `ppvzSupplierInn` — string **обязательный**. ИНН партнёра
- `declarationNumber` — string **обязательный**. Номер таможенной декларации
- `bonusTypeName` — string. Виды логистики, штрафов и корректировок ВВ
- `stickerId` — string **обязательный**. Стикер МП
- `country` — string **обязательный**. Страна продажи
- `srvDbs` — boolean **обязательный**. Признак услуги платной доставки
- `penalty` — string **обязательный**. Общая сумма штрафов
- `additionalPayment` — string **обязательный**. Корректировка Вознаграждения Вайлдберриз (ВВ)
- `rebillLogisticCost` — string **обязательный**. Возмещение издержек по перевозке/по складским операциям с товаром
- `rebillLogisticOrg` — string. Организатор перевозки
- `paidStorage` — string **обязательный**. Хранение
- `deduction` — string **обязательный**. Удержания
- `paidAcceptance` — string **обязательный**. Операции на приёмке
- `orderId` — integer **обязательный**. ID сборочного задания
- `kiz` — string. Код маркировки [Честного знака](https://честныйзнак.рф/)
- `isB2b` — boolean **обязательный**. Признак B2B-продажи
- `trbxId` — string **обязательный**. ID короба для обработки товара
- `installmentCofinancingAmount` — string **обязательный**. Скидка по программе софинансирования
- `wibesDiscountPercent` — number **обязательный**. Скидка Wibes, %
- `cashbackAmount` — string **обязательный**. Сумма, удержанная за начисленные баллы программы лояльности
- `cashbackDiscount` — string **обязательный**. Компенсация скидки по программе лояльности
- `cashbackCommissionChange` — string **обязательный**. Стоимость участия в программе лояльности
- `paymentSchedule` — string **обязательный**. Разовое изменение срока перечисления денежных средств
- `deliveryMethod` — string **обязательный**. Способ продажи и тип товара
- `sellerPromoId` — integer **обязательный**. ID собственной акции продавца с дополнительной скидкой
- `sellerPromoDiscount` — number **обязательный**. Размер дополнительной скидки по собственной акции продавца, %
- `loyaltyId` — integer **обязательный**. ID скидки лояльности от продавца
- `loyaltyDiscount` — number **обязательный**. Размер скидки лояльности от продавца, %
- `uuidPromocode` — string **обязательный**. ID промокода
- `salePricePromocodeDiscountPrc` — number **обязательный**. Скидка за промокод, %
- `articleSubstitution` — string **обязательный**. ID подменного артикула
- `salePriceAffiliatedDiscountPrc` — number **обязательный**. Скидка по подменному артикулу, %
- `agencyVat` — number. Удержание Агентского НДС, %. Только для продавцов из Кыргызстана
- `salePriceWholesaleDiscountPrc` — number **обязательный**. Оптовая скидка для бизнеса, %
- `b2bCustomerTin` — string **обязательный**. ИНН B2B-покупателя
- `paidWithSocialCertificate` — boolean **обязательный**. Оплата социальным сертификатом
- `warehouseLogisticsCoeff` — number **обязательный**. Коэффициент логистики
- `orderUid` — string **обязательный**. ID корзины заказа — транзакции. Заказы в одной корзине покупателя будут иметь одинаковый `orderUid`
- `srid` — string **обязательный**. ID заказа. В ответах методов сборочных заданий [FBS](./orders-fbs#tag/Sborochnye-zadaniya-FBS), [DBW](./orders-dbw#tag/dbwAssemblyOrders), [DBS](./orders-dbs#tag/dbsAssemblyOrders) и [Самовывоз](./in-store-pickup#tag/inStorePickupAssemblyOrders) `srid` равен `rid`

**204** — Нет данных

**400** — Неправильный запрос

- `status` — integer. HTTP статус-код
- `title` — string. Заголовок ошибки
- `detail` — string. Детали ошибки
- `requestId` — string. ID запроса
- `origin` — string. ID внутреннего сервиса WB

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
