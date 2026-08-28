---
title: Отчёт о возвратах
api: ozon-seller
method: POST
path: /v2/report/returns/create
operation_id: ReportAPI_ReportReturnsCreate
tags:
  - ReportAPI
spec_version: 2.1
source: "https://docs.ozon.ru/api/seller/"
deprecated: false
content_sha: fbd71ad428dee837
---

# Отчёт о возвратах

`POST /v2/report/returns/create`

Метод для получения отчёта о возвратах FBO и FBS.

## Параметры

| Имя | Где | Тип | Обяз. | Описание |
|---|---|---|---|---|
| `Client-Id` | header | string | да | Идентификатор клиента. |
| `Api-Key` | header | string | да | API-ключ. |

## Запрос

**Тело запроса** (`application/json`):

- `filter` — object **обязательный**. Фильтр.
  - `date_from` — string<date-time> **обязательный**. Дата, с которой данные отображаются в отчёте. Доступно только за последние три месяца.
  - `date_to` — string<date-time> **обязательный**. Дата, по которую данные отображаются в отчёте. Доступно только за последние три месяца.
  - `delivery_schema` — string (FBS, FBO, ALL). Фильтр по схеме работы: - `FBS` — возвраты на свой склад. - `FBO` — возвраты на склад маркетплейса. - `ALL` — все возвраты.
  - `status` — string (DisputeOpened, OnSellerApproval, ArrivedAtReturnPlace, OnSellerClarification, OnSellerClarificationAfterPartialCompensation, OfferedPartialCompensation, ReturnMoneyApproved, PartialCompensationReturned, CancelledDisputeNotOpen, Rejected, CrmRejected, Cancelled…) **обязательный**. Фильтр по статусу возврата: - `DisputeOpened` — открыт спор с покупателем; - `OnSellerApproval` — на согласовании у продавца; - `ArrivedAtReturnPlace` — в пункте выдачи; - `OnSellerClarification` — на уточнении у продавца; - `OnSellerClarificationAfterPartialCompensation` — на уточнении у продавца после частичной компенсации; - `OfferedPartialCompensation` — предложена частичная компенсация; - `ReturnMoneyApproved` — одобрен возврат денег; - `PartialCompensationReturned` — вернули часть денег; - `CancelledDisputeNotOpen` — возврат отклонён, спор не открыт; - `Rejected` — заявка отклонена; - `CrmRejected` — заявка отклонена Ozon; - `Cancelled` — заявка отменена; - `Approved` — заявка одобрена продавцом; - `ApprovedByOzon` — заявка одобрена Ozon; - `ReceivedBySeller` — продавец получил возврат; - `MovingToSeller` — возврат на пути к продавцу; - `ReturnCompensated` — продавец получил компенсацию; - `ReturningToSellerByCourier` — курьер везёт возврат продавцу; - `Utilizing` — на утилизации; - `Utilized` — утилизирован; - `MoneyReturned` — покупателю вернули всю сумму; - `PartialCompensationInProcess` — одобрен частичный возврат денег; - `DisputeYouOpened` — продавец открыл спор; - `CompensationRejected` — отказано в компенсации; - `DisputeOpening` — обращение в поддержку отправлено; - `CompensationOffered` — ожидает вашего решения по компенсации; - `WaitingCompensation` — ожидает компенсации; - `SendingError` — ошибка при отправке обращения в поддержку; - `CompensationRejectedBySla` — истёк срок решения; - `CompensationRejectedBySeller` — продавец отказался от компенсации; - `MovingToOzon` — едет на склад Ozon; - `ReturnedToOzon` — на складе Ozon; - `MoneyReturnedBySystem` — быстрый возврат; - `WaitingShipment` — ожидает отправки.
- `language` — string. Язык ответа: - `RU` — русский, - `EN` — английский. По умолчанию: `DEFAULT`.

## Ответы

**200** — Отчёт о возвратах FBO и FBS

- `result` — object. Результаты запроса.
  - `code` — string. Уникальный идентификатор отчёта. По нему вы можете получить отчёт в течение 3 дней после запроса. Чтобы получить отчёт, передайте это значение в метод [/v1/report/info](#operation/ReportAPI_ReportInfo).

**400** — Неверный параметр

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**403** — Доступ запрещён

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**404** — Ответ не найден

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**409** — Конфликт запроса

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.

**500** — Внутренняя ошибка сервера

- `code` — integer<int32>. Код ошибки.
- `details` — array[object]. Дополнительная информация об ошибке.
  - `typeUrl` — string. Тип протокола передачи данных.
  - `value` — string<byte>. Значение ошибки.
- `message` — string. Описание ошибки.
