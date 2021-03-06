# CommerceCoupons
Купоны для Commerce  на базе модуля управления таблицами webixTable (https://github.com/webber12/webixtable)

Компонент состоит из аддона для модуля webixTable и плагина для Commerce.

# Возможности аддона:

- Генерация купонов, в том числе автоматическая
- Возможность задать дату начала и окончания действия купона (группы купонов - при генерации)
- Возможность задать скидку в % либо в фикс. сумме
- Активные/неактивные купоны
- Возможность задать для купона лимит покупок с его применением (по-умолчанию 1)
- Группировка купонов по смысловым категориям (имя купона при генерации)
- Возможность задать длину купона
.. ну  ит.п.


# Задача плагина: максимально упростить использование сгенерированных купонов.
- прослушивание событий добавления купона в корзине (возможно задать перечень страниц для прослушивания)
- пересчет итоговой суммы корзины с учетом скидки в % (приоритет) либо фикс суммы
- подсчет статистики (занесение информации о связке "номер заказа - номер купона" в отдельную таблицу
- удаление данных о купоне из сессии после совершения заказа пользователем


# Использование на фронте:
- Добавить атрибут data-commerce-coupon к полю, куда будет вводиться номер купона
- Добавить атрибут data-commerce-coupon-add к кнопке "Применить купон"

# Дополнительные js-события
- при действии с купонами генерируются дополнительные js-события
- commerce-coupon-empty - пользователь не ввел купон в поле, но нажал на кнопку
- commerce-coupon-error-unactive - данный купон не активен либо не найден в базе либо по нему истекли сроки
- commerce-coupon-error-limits - по данному купону исчерпан лимит заказов
- commerce-coupon-ok-add - купон добавлен в корзину

Соответственно, данные события можно прослушивать и добавлять свои действия, например
```
<script>
$(document).ready(function(){
    $(document).on("commerce-coupon-ok-add", function(){
        alert("Купон успешно добавлен, скидка учтена");
    })
}
</script>
```

# Ограничения
- требуется версия MySQL >=5.6




