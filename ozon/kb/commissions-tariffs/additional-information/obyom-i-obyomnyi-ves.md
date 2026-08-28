---
title: Расчёт объёма и объёмного веса товара
marketplace: ozon
kind: article
path: /commissions-tariffs/additional-information/obyom-i-obyomnyi-ves
source: "https://seller-edu.ozon.ru/libra/commissions-tariffs/additional-information/obyom-i-obyomnyi-ves"
updated: "2026-02-18 07:09:26"
doc_id: 689
fetched_at: "2026-08-28T12:11:14Z"
content_sha: 4c10b956bc7a5a24
---

# Расчёт объёма и объёмного веса товара

_Главная / Комиссии и тарифы / Дополнительные материалы_

Где в Ozon используем объём и объёмный вес товара и как их рассчитать

# Как мы рассчитываем объём и объёмный вес

Делаем это автоматически по [объемно-весовым характеристикам (ОВХ)](/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/ovh), которые вы указали при создании или редактировании карточки товара:

«Вес с упаковкой, г»;

«Ширина упаковки, мм»;

«Высота упаковки, мм»;

«Длина упаковки, мм».

Когда укажете вес и габариты товара, система рассчитает:

**объём** — отобразим на странице **[Аналитика → Отчёты → Товары](https://seller.ozon.ru/app/analytics/fulfillment-reports/all-products)** в отчёте по товарам в столбце **Объём товара, л**. Минимальное значение — 0,01 л.;

**объёмный вес** — отобразим в разделе **[Товары → Список товаров](https://seller.ozon.ru/app/products)** в столбце **Объёмный вес, кг**. Минимальное значение — 0,1 кг. Если объёмный вес окажется меньше, округлим его до минимального значения.

# Как посчитать объём и объёмный вес самостоятельно

Подготовили для вас калькулятор расчёта — просто укажите ОВХ товара и получите его объём и объёмный вес:

[Скачать калькулятор расчёта объёма и объёмного веса в Excel](https://cdn.ozone.ru/s3/ozon-disk-api/Seller-edu/files/commissions-tariffs/raschitat-obyomniy-ves/kalkulyator-obyomyi-i-obemnyi-ves_1713432737.xlsx)

1. Измерьте для товара:
  [фактический вес](/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/ovh#%D0%BA%D0%B0%D0%BA-%D0%BF%D1%80%D0%B0%D0%B2%D0%B8%D0%BB%D1%8C%D0%BD%D0%BE-%D0%B8%D0%B7%D0%BC%D0%B5%D1%80%D0%B8%D1%82%D1%8C-%D0%B2%D0%B5%D1%81);
  
  [габариты](/work-with-goods/trebovaniya-k-kartochkam-tovarov/product-information/ovh#%D0%BA%D0%B0%D0%BA-%D0%BF%D1%80%D0%B0%D0%B2%D0%B8%D0%BB%D1%8C%D0%BD%D0%BE-%D0%B8%D0%B7%D0%BC%D0%B5%D1%80%D0%B8%D1%82%D1%8C-%D0%B4%D0%BB%D0%B8%D0%BD%D1%83-%D1%88%D0%B8%D1%80%D0%B8%D0%BD%D1%83-%D0%B8-%D0%B2%D1%8B%D1%81%D0%BE%D1%82%D1%83).
2. Посчитайте объём в литрах по формуле:
  **Длина, мм** x **Ширина, мм** x **Высота, мм** / 1 000 000
3. Разделите объём товара в литрах на 5.
4. Сравните с фактическим весом товара в кг и выберите большее значение — это и будет объёмный вес товара.

Пример расчёта:

| **Что рассчитываем** | **Товар № 1** | **Товар № 2** |
| --- | --- | --- |
| **Фактический вес, кг** | 3,1 | 3,8 |
| **Габариты, мм** | 230 х 100 х 500 | 300 х 100 х 700 |
| **Расчёт объёма, л** | (230 * 100 * 500)/1000000 = 11,5 | (300 * 100 * 700)/1000000  = 21 |
| **Объём, л** | 11,5 | 21 |
| **Расчёт объёмного веса, кг** | 11,5 л / 5 = 2,3 Фактический вес: 3,1 Большее значение: 3,1 | 21 л / 5 = 4,2 Фактический вес: 3,8 Большее значение: 4,2 |
| **Объёмный вес, кг** | 3,1 | 4,2 |

# Где используем объём и объёмный вес товара

Для расчёта логистики и услуг на площадке используем разные единицы измерения у товаров. Полный перечень услуг, которые тарифицируем в зависимости от объёмного или фактического веса и объёма можно посмотреть в разделе [«Расходы на другие услуги»](/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi).

| **Единица измерения** | **В каких расчётах используется** | **Что означает** | **Где отображается** |
| --- | --- | --- | --- |
| **Фактический вес** кг | Для определения стоимости [утилизации товара](/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi#утилизация-товаров) на схеме FBO | Отражает только массу товара | В личном кабинете при [редактировании карточки товара](/work-with-goods/zagruzka-tovarov/created-goods/editing-products) |
| **Объём** литры | Для определения стоимости: **• **[размещения](/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi#размещение) на складах Ozon; **• **[логистики](/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dostavku) и [обратной логистики](/commissions-tariffs/commissions-tariffs-ozon/rashody-na-otmenu-vozvraty) на схемах FBO и FBS; **• **прочих [логистических услуг](/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi#логистические-услуги); **• **услуг [приёмки](https://seller-edu.ozon.ru/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dop-uslugi#%D0%BF%D1%80%D0%B8%D1%91%D0%BC%D0%BA%D0%B0) и вывозов. | Позволяет узнать, сколько места занимает товар | **• **В личном кабинете при [редактировании карточки товара](/work-with-goods/zagruzka-tovarov/created-goods/editing-products) **• **На странице **[Аналитика → Отчёты → Товары в отчёте](https://seller.ozon.ru/app/analytics/fulfillment-reports/all-products)** по товарам в столбце **Объём товара, л.** |
| **Объёмный вес** кг | Для определения [стоимости доставки партнёрами Ozon](/commissions-tariffs/commissions-tariffs-ozon/rashody-na-dostavku) на схеме realFBS Standard | Позволяет учитывать и объём (габариты), и массу товара | В разделе **[Товары → Список товаров](https://seller.ozon.ru/app/products)** в столбце **Объёмный вес, кг** |
