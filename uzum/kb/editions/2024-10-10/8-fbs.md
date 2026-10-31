---
title: 8. Работа с заказами по FBS
marketplace: uzum
kind: article
path: /editions/2024-10-10/8.fbs/
source: "https://seller.uzum.uz/manual/editions/2024-10-10/8.fbs/"
fetched_at: "2026-10-31T02:49:36Z"
content_sha: 2d19fdad7bc923e1
---

# 8. Работа с заказами по FBS

FBS (fulfilment by seller) — это формат работы с маркетплейсом, при котором вы храните товары на своём складе, сами собираете, упаковываете их для доставки и передаёте заказы в наш распределительный центр. А мы доставляем их покупателям по всей стране.

## Создание товара

- Чтобы начать продавать по системе FBS создайте карточки товара.
- Вы можете продавать один и тот же товар и с нашего склада и со своего (дублировать карточку товара для продажи по FBS нельзя)

> Важно учесть, что если у вас есть остаток на FBO, то на витрине мы показываем остаток на нашем складе. Когда он заканчивается, мы переключаем остаток на FBS. Если на FBO снова появился остаток, то мы переключаем на него даже если по FBS есть остаток. Т.е. остаток товара по FBO приоритетнее для продажи.

Категории, которые нельзя продавать по FBS: Продукты питания (исключение: спортивное питание)\

После того как вы определились с ассортиментом: у вас готовы карточки товаров и по ним пройдена модерация (Статус модерации "Пройден") вы можете обновить остатки

## Остатки по товарам

### Обновление остатков

1. После того, как вы завели карточки товара, и по ним пройдена модерация, вы можете указать остаток на вашем складе
2. Перейдите в раздел "Товары". Нажмите на кнопку "Обновить остатки FBS". Выгрузите файл с товарами и проставьте остаток в колонке "Остаток FBS". В файл выгрузятся товары, которые прошли модерацию и разрешенной категории для продажи по FBS

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfmpg9jKezP51RkKey4frIFh8LuXFkccgWxoVDz-8muhUZtHrzURiM4K0JcKzPDOFfafYdniAkP3bWmBlT143n55BboJtOcvguYnXv9bDrhHO6-1fPxsG-yylzGuCXS8YwobXXV1QovC9gMlQ8q24FPhRb_?key=ajFkOVe7ToRa5SgFtBJApg)][]

Обновление остатков в разделе "Товары"

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXehcgyvaKQWgOgVVgO79OfayWjDWAH47AGpP3dQyVrGHzwznztC5_-1JgsGMENBnnxEKdF4lcQFg8XVB2RAQ3vTwNAvz0d2B5nzPOoBWAU9koB6EIBn4V6mzNxNfo2OJz_nA2CCNvm-gg1T2EC7jpXxiXFv?key=ajFkOVe7ToRa5SgFtBJApg)][]

Скачивание файла

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdhhf4cDJ_LoYXc07hcPAUq1hNu8dh2ePNMCpscIZ17U_NRcseUB8-BaqiBMYoa56nUPmAKdASvIotFjg1DVLIoU-LpX58D3Vg9wWIUL4cbiU-_hvOwz_7k1eSPUhnHClAWDbs0Fb_EvgVWnUKaEKBtda0j?key=ajFkOVe7ToRa5SgFtBJApg)][]

Обновление остатков

1. Если товар закончился, проставьте 0
2. Загрузите в модальное окно файлик
3. После загрузки остаток обновится по SKU

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdYirYC6xQ6e1mvDDMkpvtuufvW17yBfNNix1oeQnJOp1JesZswsQNE-_1X-I9usAwTZgTDIWUbQffvaolgN4-aL_nTNxnG5mntTPoqzrrT9-2KWebhy_vmITF6aI1qhDYbK39na4JGPZwTG3k8DeEdumac?key=ajFkOVe7ToRa5SgFtBJApg)][]

Остаток по FBS

### Как считается остаток

- Из вашего остатка мы вычитаем только то количество единиц, которые попали в заказ и выданы покупателю
- Если заказ отменил покупатель после оформления, мы вернемся количество в остаток
- Если заказ отменили вы или покупатель вернул товара на ПВЗ или не пришел за ним, мы не вернем это количество в остаток

> Поэтому следите и регулярно обновляйте остаток

## Настройка склада

Для начала работы перейдите в раздел FBS, нажмите на значок настройки, и настройке график работы вашего склада.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfk4DXdJWx78g8J1D1POw8jodP7NcaQwATaqKSH19JVRfsfQx31GEJQ0zA7DeFRKOYsuCfJlogrHZzVUb55iG7LO_3ftcgku-IVDc9yR7X_t3bxzv3KDWgb_cH83MxlMbq7oldIdENMW70486u6P9B9G4bh?key=ajFkOVe7ToRa5SgFtBJApg)][]

Выберите рабочие дни склада - не менее 5 дней. Заказы могут поступать в любое время, но время доставки для них будет рассчитано с учетом ваших выходных дней.

Заказы, поступившие до 15:00 будут учитываться в сегодняшний день

Любые изменения в графике применимы для новых поступивших заказов. Заказы, созданные до установки или изменения графика необходимо обработать в установленное время. Дата доставки по ним не будет пересчитана.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXc1w12b5zYI5-JMB0wRRj9fJqtXb-KcG3iB3M7hlSaHMPoeYnRF-QhFV9JaS2roCs90nNxx5RbJNqibfMdj3V-c2fH5sLcXPmj3KoOMY6cMaCZLJqakCKYbSEqkJdHQYbG4o4-wIBedyy1H9kNwfdvsjVkJ?key=ajFkOVe7ToRa5SgFtBJApg)][]

Примеры расчета даты "Доставить до":

Время, до которого заказы учитываются в сегодняшний день: 15:00

Время приемки нашего склада: до 16:00

1. Заказ оформили в вторник 01.10 19:00

- Мы прибавляем к вторнику 01.10 +2 дня (четверг 03.10) + след.день рабочий селлера + время до катофа = пятница 04.10 18:00
- без выходных
- Дата доставить до пятницы 04.10 16:00

1. Заказ оформили в пятницу 04.10 23:00

- Мы прибавляем к пятнице 04.10 +2 дня (воскресенье 06.10 ) + след.день рабочий селлера + время до катофа = понедельник 07.10 18:00
- без выходных
- Дата доставить до пятницы 07.10 16:00

1. Заказ оформили в среду 02.10 19:00

- Мы прибавляем к среде 02.10 +2 дня (пятница 04.10 ) + след.день рабочий селлера + время до катофа = суббота 05.10 18:00
- Суббота и воскресенье выходные
- Дата доставить до понедельника 07.10 16:00

1. Заказ оформили в пятницу 04.10 в 14:59

- Мы прибавляем к пятнице 04.10 +2 дня (воскресенье 06.10) + время до катофа = воскресенье 06.10 16:00
- Если считать, что воскресенье выходной: + след.рабочий день селлера + время до катофа = пятница 07.10 18:00
- Дата доставить до воскресенья 06.10 16:00

1. Заказ оформили в пятницу 04.10 в 14:59

- Мы прибавляем к пятнице 04.10 +2 дня (воскресенье 06.10) + время до катофа = воскресенье 06.10 16:00
- Если считать, что воскресенье выходной: + след.рабочий день селлера + время до катофа = понедельник 07.10 18:00
- Дата доставить до понедельника 07.10 16:00

1. Заказ оформили в воскресенье 06.10 16:00

- Мы прибавляем к воскресенью 06.10 +2 дня (вторник 08.10) + след. рабочий день селлера + время до катофа = среда 09.10 18:00
- Среда и пятница выходные
- Дата доставить до четверга 10.10 16:00

1. Заказ оформили в СР 02.10 17:00

- Мы прибавляем к среде 02.10 +2 дня (пятница 04.10) + след. рабочий день селлера + время до катофа = суббота 05.10 18:00
- Средна и пятница выходные
- Дата доставить до субботы 05.10 16:00

1. Заказ оформили в среда 02.10 14:00

- Мы прибавляем к среде 02.10 +2 дня (пятница 04.10) + время до катофа = пятница 04.10 16:00
- Среда и пятница выходные
- Дата доставить до субботы 05.10 16:00

## Работа с заказами

Для начала работы с заказами перейдите в раздел FBS

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdCvd7I3zNj3Cv1ZIV_DH8ox1EMnll-M0wiQv_qmTVOgzNiYHjE0JwHbNfK6fYrqN7roBbPJbPd6vRKk-CxBx7BcPMivgKXAHMRwM_JFfhEWiTXT-B-Q44wVPBSOxhuw_kXd_P7hwJ_HIdemM2vQIZnaBU?key=ajFkOVe7ToRa5SgFtBJApg)][]

### Новые заказы

- На вкладке "Новые" отображаются новые заказы, которые необходимо взять в работу.
- Заказы отсортированы по дате создания: от старых к новым
- Подтвердить до - время, до которого необходимо взять заказ в работу. В течение 16 часов с момента создания заказа подтвердите, что вы увидели заказ, у вас есть товары в наличии и вы привезете его на склад.
- Чтобы посмотреть подробную информацию по заказу нажмите на него - откроется модальное окно.
- Чтобы взять заказ в работу, нажмите "Взять в работу". После этого он перейдет в статус "В сборке" и отобразится на соответствующей вкладке

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfZsYvUtaCR4drI780lFC4Ef8SA3H-8kfHLpcNe89pUcBtNEVT_AAXwaLBIfJ2ZiAdrseg_FZISDuGP6xEY-MxUDg0Wi3KIasYEthlVyImiXdA7UaFm0XtP4eP0iBV0_ClzGTeIdIyRBITrLGz3fV6VQlSu?key=ajFkOVe7ToRa5SgFtBJApg)][]

Список новых заказов

### Отмена заказа

Если по какой-либо причине вы не сможете доставить заказ, нажмите на крестик "Отказаться от заказа" либо в модальном окне "Отказаться"

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeeKUWZFqadPLfam5lBI3PaUzqyggjJFKox-w1KGBsHfKP8ia0nEl7TZo1GZlISKfxfdGLQdqvBbP5JbMZ02H4l73xRIUYQdRCjNZ4EfYhbgMtpoxs8k-NiP_clMdkjWuYeefmVSQtg8aKFMNx4fOkJICH1?key=ajFkOVe7ToRa5SgFtBJApg)][]

Отмена в списке заказов

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdiAEQXKWuXQoOjAVpIpks9CQi_103lWGftAaouGM1Sk4CsSTRTF5nXgAFqcfZohnVMpcV8JfzW5NYKIqPpNPS3K8_4elOTUZdSyjssjGDXwsnCc9JR_TADgfJNDefDUvgk7HyNFz5HAbMN27KtHBcj92g?key=ajFkOVe7ToRa5SgFtBJApg)][]

Модальное окно

Выберет причину, по которой вы не сможете доставить заказ

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcdzzYcTFgqrTuq3yhmA4K9oWl8ShsHO9a_RbVxjsFepVwsIlyh35-vJ182vhlrROeNDK3HQw4Ap9fKXzanwFn8rBWQfpPmUYootDJd4nt3SbxO75SvdW_f5_n3fHTJ2rMte4xG1LkR7ySi9lyzKEYN1JM?key=ajFkOVe7ToRa5SgFtBJApg)][]

Причины отмены заказа

После отмены, заказ перейдет на вкладку "Отменены"

> Отмена заказа - плохо. Вы теряете доверие покупателя, что влияет на ваш рейтинг и дальнейшие продажи. Поэтому вовремя пополняйте остатки и соблюдайте сроки.

### Сборка и доставка заказов

После взятия в работу заказ переходит в статус "В сборке" и отображается на вкладе "В сборке".

На этом этапе вам необходимо собрать ваши заказы:

1. Наклеить штрихкод на каждый товар
2. Наклеить маркировку ASL Belgisi, если необходимо и ввести код маркировки в заказе для каждого товара
3. Упаковать
4. Наклеить этикетку
5. Создать накладную
6. Отвезти на склад

> Обратите внимание на дату и время "Доставить до" - это то время, до которого вы должны привезти заказы на склад. У вас есть 48 часов + время до катофа на складе. Если заказы не будут доставлены до этого времени, заказ отменится.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdbdtndSBBFHOz6py1ytmYYgVv3d68acrKl9W-wKTQfP-dhXJZEJdVvcxhlxA3TYVo1CUsY3qtF5PAHOARhs4iMlZ_MV5DTdF1JcGSvETVn8zU6LFR1oHnd6y-FyVcRkPa_40iWMJauGbg8D2-AAl-Jsgmy?key=ajFkOVe7ToRa5SgFtBJApg)][]

### Штрихкод

На каждый товар в заказе должен быть наклеен штриход (как и при обычной поставке на склад)

Для этого перейдите в раздел "Этикетки", выберете SKU, распечатайте штрихкоды и наклейте на товары.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdXFpeZR-oi4QiNsbPUJ_ojgDYA-TMdpL3u1Eht4nKEoVMWP1RieY0RORWfJnPvsQaVkoANtbDjgHjmENp8YPhX5x4VR-KxzBxoRcg4vqgWxP22g2WybTMuKEp2jN3rt6C_IGsAg7UOpdOjYZR8fBIieKdq?key=ajFkOVe7ToRa5SgFtBJApg)][]

### Маркировка

- Для некоторых категорий товаров необходима маркировка: ASL Belgisi (бытовая техника) или IMEI (телефоны)
- Код должен быть проставлен для каждой единицы товара
- Без заполненной маркировки вы не сможете распечатать этикетки и отправить товары на склад

1. Если около товара в списке заказа стоит значок маркировки, то ее необходимо заполнить. Заполнить можно на этапе "В сборке"

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfFFKXSR0YMsfPso2PunZFvrfkq1NYKygEoAEel3oykev1ohzayUv-2Iw-YxrqaHBP1_A0KLWnPEHg-Tnc_4Aw1uRjuEfD_gwX-BsYYqyM_vnb0J6fqaesSBgQbPaND4dhp_hF5nCrbJE2ZIH5XkBkIiww?key=ajFkOVe7ToRa5SgFtBJApg)][]

1. Перейдите в модальное окно заказа и нажмите на "Добавить маркировку" или редактирование маркировки::: пример [https://lh7-rt.googleusercontent.com/docsz/AD_4nXeYrH-SSztqh-xFmonjoKSTxbxOrJ_1xCHW1IAd4fwfLP80E3h6hZj_vND6w0lnqMMjx13g-5JEW2YEv7gp63ZzS9HsCBmeW2rqJxIUNmmzm_vnsEfQxpdThMNopKsx5qtVd6Hb8HR87xlGtfvgBsRzhp4N?key=ajFkOVe7ToRa5SgFtBJApg](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeYrH-SSztqh-xFmonjoKSTxbxOrJ_1xCHW1IAd4fwfLP80E3h6hZj_vND6w0lnqMMjx13g-5JEW2YEv7gp63ZzS9HsCBmeW2rqJxIUNmmzm_vnsEfQxpdThMNopKsx5qtVd6Hb8HR87xlGtfvgBsRzhp4N?key=ajFkOVe7ToRa5SgFtBJApg)

Нажмите "Добавить маркировку"

1. Откроется модальное окно с заполнение маркировки. Если в заказе несколько единиц товара, то для каждого из них необходимо ввести код.

#### ASL Belgisi

Подробная инструкция для каждой категории товара описана на сайте [https://help.crpt-turon.uz/hc/ru](https://help.crpt-turon.uz/hc/ru)

> Также мы можете использовать различные приложения для распознавания кода маркировки

- На каждом товаре должна быть наклеена маркировка DataMatrix
- Код, введенный для каждой единицы товара должен соответствовать DataMatrix.
- Вам необходимо ввести весь код маркировки

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcdP6LO3G7dzqOGcAX18mjb7edjj4AcZIHnuJTsxiC-THEMl9MulUqxfNl_2Pw3pB4DNFIfzAUzcsa2smduBME2rgitfMk5THbdZWCa1imqXdZ2g49k0PSGFkm0NANG-TdL3GLtr-xEI5-ti8aG0VWtEtU?key=ajFkOVe7ToRa5SgFtBJApg:::%20пример%20https://lh7-rt.googleusercontent.com/docsz/AD_4nXeNK41VeljyFP1K0CQpnsBRmTaIU2VC7ZJK69msJzqnoSNzlvQIQ2wrzHhTYvWBQqZE5W4eulnHkvUNWxjxak-yJho-8z2jWnaB-TJO-z8hIWYfJ_DCk_N1NDDwUOskDdyAYESonKikryIjdpQ41ztQ1nk?key=ajFkOVe7ToRa5SgFtBJApg)][]

> Данный код вводится в оборот, печатается на чеке, а так же проверяется при возврате товара покупателем. Мы проверим, что код соответствует, указанному в карточке заказа.

#### IMEI

> Данный проверяется при возврате товара покупателем. Мы проверим, что код соответствует, указанному в карточке заказа.

- IMEI всегда указан на заводской упаковке товара и на самом товаре
- Код вводится для каждой единицы товара

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfqXefjszV92z_k8P7_UKd62mSK3h1FSPkUPD6lzhQo6Ml0jzUDNGRHC3vXZG98zULwBWI02v-nCbRe3DQHsR2kWKuldS56BeoFY0yMQOMhDld-SreHqCEyOOKWwWOQIbAebSUBwxelPjDysh4GfmQNilfh?key=ajFkOVe7ToRa5SgFtBJApg)][]

### Упаковка

- Убедитесь, что товары (в том числе заводская упаковка) не повреждены
- Внимательно проверяйте упаковку перед отгрузкой. Сохранность товаров в заказе зависит от вас. Uzum Маркет не компенсирует повреждения или потерю товара во время доставки, если он был упакован неправильно.
- Если повреждения заметны сотрудники пунктов выдачи и сортировочных центров имеют право не принять заказ.

#### Правила упаковки

1. Ценные: Компьютеры и комплектующие, телефоны, аудио- и видеотехника, ювелирные изделия, наручные и карманные часы и ТД. Перед тем как упаковать товар в коробку заверните его в воздушно-пузырчатую пленку. Заклейте прозрачным скотчем.

2. Хрупкие: Товары, которым нужна специальная защита от падений, вибрации, ударов или давления:

a. Это изделия из стекла, пластика, керамики, акрила, гипса, фарфора, фаянса, хрусталя, тонкого металла или изделия, покрытые эмалью.

b. Декоративные изделия и косметика. В пакеты с воздушно-пузырчатой пленкой и в стрейч пленку.

c. Товары больше 60 × 50 × 50 см или тяжелее 30 кг упакуйте в воздушно-пузырчатую пленку и обмотайте стрейч пленкой. На упаковке должны быть манипуляционные знаки «Хрупкое. Осторожно»

3. С выступающими или острыми частями. Например, самокаты, стулья, шкафы, тумбочки, швабры, мангалы, шампуры, антенны и т. п. В стретч-пленку и впупырчатую пленку:

a. Выступающие части или углы дополнительно оберните в один слой воздушно-пупырчатой пленки

4. Жидкости. Стеклянные банки или бутылки, спайки стеклянных или жестяных банок и упаковки дой-пак обмотайте пупырчатой пленкой, поверх нее стретч-пленкой так, чтобы защитить горлышко. Тара должна стоять в коробке строго горлышком вверх. На упаковке с любыми жидкостями должен быть манипуляционный знак «Верх».

5. Сыпучие. Например, крупы, земля, грунт, корма для животных . В плотный прозрачный зип-пакет или стретч-пленку.(2-3 слоя)

6. Одежда и обувь. В прозрачный зип-пакет или в стрейч пленку.(2-3 слоя). Если товар в заводской коробке, можно в стретч-пленку.

7. Чемоданы. Закрепите заводской пакет скотчем. Если пакета нет обмотайте стретч-пленкой.

8. Упаковка КГТ и МГТ заказы (Крупногабаритный и мелкогабаритный товар): Если в заказе присутствует КГТ и мелкий товар, то мелкий товар упаковывается в спец пакет и клеится стикер после прикрепляется стрейч-пленкой к КГТ. (С инфо листом, заказ состоит из двух и более частей)

9. Упаковка КГТ (Крупно Габаритный Товар): КГТ аккуратно упаковывается в стрейч-пленку.

10. Упаковка заказов с присутствием химии и пищевых продуктов: Если в заказе присутствует товары домашней или прочей химии и пищевые продукты питания, следует разделить заказ в разные пакеты, но упаковка для заказа все равно должна быть одна

Важно !!!

Все товары должны быть упакованы в прозрачные пакеты .

Пакеты должны быть больше товара (минимальное ограничение от 15х15 см и максимальное 80х120х160 см)

### Этикетка

- Для печати этикетки нажмите на "Печать этикетки". Откроется экран печати. ::: пример [https://lh7-rt.googleusercontent.com/docsz/AD_4nXfoVgn_BJa-GOMGhAHKqJ-i7M1uatOOT9B4fEGW1IWKc5fOoVN3494aGmB4oyLfNiSUzthQ52OCdxP1QhBuQs5DqcgoYsYNwJRbIsnmvLDMs1zhGutp1MaMJSjc6KnmJbvnEtcXqT5d36OJMnOlAuiutxo?key=ajFkOVe7ToRa5SgFtBJApg](https://lh7-rt.googleusercontent.com/docsz/AD_4nXfoVgn_BJa-GOMGhAHKqJ-i7M1uatOOT9B4fEGW1IWKc5fOoVN3494aGmB4oyLfNiSUzthQ52OCdxP1QhBuQs5DqcgoYsYNwJRbIsnmvLDMs1zhGutp1MaMJSjc6KnmJbvnEtcXqT5d36OJMnOlAuiutxo?key=ajFkOVe7ToRa5SgFtBJApg)
- Размеры этикеток на выбор: 43*25 или 30*20
- Этикетка с номером ПВЗ и Направлениями должны быть наклеена строго по середине (используем термопечать, не должно быть не пропечатанных линий)
- Если нет термопечати, напечатайте согласно размеру выше на обычном листе и приклейте прозрачным скотчем всю область этикетки.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdWchp5YevqIelLtjx0yDPqEAqIL7wDpRcrYuO3G0dSKvt7u1NqV0rolNz9euVwJqab7neb75Go4oiiCoOZSdtHaqsi9IeK6Wkq9mJkjwNDqKnXrMtNn0wu3IgRnhzOBHyzYEI8cG747eyQQxArh6M-drfO?key=ajFkOVe7ToRa5SgFtBJApg)][]

### Накладная

- После того как вы упаковали все свои заказы и готовы везти их на склад сформируйте накладную.
- Для этого выберете заказы, которые вы хотите поставить на склад, нажав на чекбокс рядом с заказом.

В одну накладную можно объединить заказы из одного магазина. Если вы хотите отправить товары из нескольких магазинов, просто создайте для них свои накладные

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXcSXyhn2MBDmZPZPZhB8uD6EbZVVIkEjhdK4j8Mkw0-EFETj7teGlYX-VdWJ7D4Y63xJcqQJFuakkbOmjoJ8VGNKDzt_lBfZDmyy1Rv6589jWH6VRv31NPC1MQxvUPWmlkN2ETtxib6LBUufNPu1hiui6LT?key=ajFkOVe7ToRa5SgFtBJApg)][]

- После нажатия на "Печать акта поставки" откроется экран с печатью.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXflTXrELNcgAqa36hNG86Kf-vWIZUnBtBpjyJsxFT5QzX57wIylDqLz6kHeC3W_dpA9TnWNEaSKIG79Ms4GhPAyCYfcI2OwaHf90vaghry8YznRZC8qs-yNenemndPb7hP_WaCYv_Y732J135wi_i84Vs3e?key=ajFkOVe7ToRa5SgFtBJApg)][]

- Так же эта накладная автоматически сохранится и отобразится в разделе "Накладные" на вкладке "Поставки заказов FBS". Здесь так же можно будет распечатать накладную.
- Накладные в разделе "Поставки заказов FBS" всегда будут в статусе "Создана". Приемку заказов отслеживать в разделе FBS.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdt_1eiWkKQSbdMb0IEqLe0OA_Q9c9gzYpKBnK02keowKzXUr9Cy7yBpdPSMlgR89GLluKSKWZsifq4NL7uTnUlpl2D7BGHMtOqmto_ILS7GwMpLfhm5xDEsly6cIRKMoOoWzA2CeZRGPdUvG1YjxW_c8Qi?key=ajFkOVe7ToRa5SgFtBJApg)][]

## Рейтинг продавца

В разделе FBS в правом верхнем углу отображается рейтинг продавца.

Он рассчитывается по юридическому лицу на основе заказов, отмененных селлером за последние 30 дней (отменил сам заказ или не привез вовремя).

Больше 10% отмен - это плохо.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdY9G572ht4J1Jl2lNOzXdoFuiTksypRu4UhQtLkRSa41BkJZKg__YMoJufanrTwY7c8VwC6IuDh3VaJo875GiFuMWwtquWkY-L4dx3MZeSjj5szrKrApILepr435Ki2wjC_UUeQj0YC2xoKp_UJoJzF4k?key=ajFkOVe7ToRa5SgFtBJApg)][]

## Поставка и приемка на складе

> Приемка товаров осуществляется на новом складе "Фулфилмент" с 9:00 до 16:00

Въехав на территорию складского комплекса, необходимо проехать прямо по бетонной дороге до второго КПП, проехав КПП повернуть налево, проехав до конца территории повернуть направо и проследовать к доковым воротам №1. и позвонить в звонок.

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXeAklKSgx76ctDxFZwFelOv8GPlXKPMk5bdgjr4KzfPpHkAlQnjo4Oilm3MiRq_-YOHt7Dx9kxP9JgsLEF5bIMTqa59JT1lJCLi9w5FyMFz8_WwZZfXIRvcvW3a6DKHSDS_3bbv8vvfZi9kONti7T2sSiaE?key=ajFkOVe7ToRa5SgFtBJApg)][]

- Убедитесь, что все заказы упакованы, на каждом заказе есть этикетка, накладная распечатана и список заказов, которые вы везете на склад должен совпадать с накладной.
- После того, как склад примет заказы у них поменяется статус в личном кабинете на "В доставке"
- Когда мы доставим товар до покупателя (=выдан покупателю) статус заказа поменяется на "Доставлен"

## Возврат

- Если покупатель вернул заказ/товар из заказа или не забрал его из ПВЗ в течение 5 дней, то в таком случае заказ перейдет в статус "Возврат"
- Товары/заказы вернутся на склад в течение 1-2 дней после оформления возврата.
- Склад соберет все ваши товары/заказы и сформирует возвратную накладную.
- Накладная с типом FBS появится в разделе "Накладные" на вкладке "Возвраты со склада" (от перехода заказ в статус "Возврат" до создания накладной может пройти несколько дней)
- Вы сможете выбрать таймслот и забрать товары в удобное для вас время

[![](https://lh7-rt.googleusercontent.com/docsz/AD_4nXdJ-Za9k5TCy0xAHfcuxXxpXuHw20Xn3uZbBnAOBMHEmAf9ENlA2kLCD7wX5yG6zdtRm63vBaXzYo5UF64V90XkiZH-R740Phs3rnENmULSQiogGMpsI6y5vdlQAPRCxvqutUva3og9WkuvLAGMy2lP93oi?key=ajFkOVe7ToRa5SgFtBJApg)][]
