 Задание 1

Есть таблица с товарами: items

item_id    name                 price       update_date
-------    ----------------     ------      -----------
1          Ручка гелевая        10          2020-02-01
2          Карандаш 1HH         2           2020-01-01
1          Ручка шариковая      10          2020-03-01
3          Ластик               5           2020-07-01
2          Карандаш 1HH         3           2020-05-01
1          Ручка шариковая      5           2020-05-01
2          Карандаш 1H          7           2020-06-01

----------------------------------------------------------------
И таблица с заказами: orders

order_id    user_id     item_id     order_date
-------    --------     -------     ----------
1           1           1           2020-02-01  10
2           2           2           2020-02-01 2
3           1           3           2020-07-01 5
4           3           2           2020-07-01 7
5           2           1           2020-04-01 10
6           1           1           2020-06-01 5


Написать запрос, который:
1. Выведет актуальное состояние товаров на 2020-06-01
2. Товары, купленные по цене больше или равно чем 3
3. Сумму покупок клиента 1
4. Сумма всех покупок до 2020-05-01 включительно
5. Сумму всех заказов и среднее цена заказа поквартально
6. Объясните, как вы будете оптимизировать запросы для больших объемов данных.

Задание 2

У нас есть поток заказов, примерно 100 000 заказов в день, которые записываются в таблицу `orders`.  
Эти данные переливаются в DWH, но есть сложность:

- В первые 6 месяцев заказы активно изменяются (например, обновляется статус, состав заказа, стоимость и т. д.).
- Далее в течение 2-5 лет возможны редкие изменения.
- Мы не можем использовать метку времени обновления (`updated_at` или аналоги).

Вопросы не подразумевают единственно верного варианта решения задачи.
Ожидаем, что вы изложите ход мысли и подробно опишете решения, ответив на следующие вопросы:

1. Как можно построить архитектуру DWH на основе Data Vault 2.0, чтобы:
    - Обеспечить актуальность данных (иметь "актуальную" таблицу заказов).
    - Эффективно хранить изменения, учитывая разные паттерны обновлений.
    - Не терять историчность (возможность "путешествовать" во времени).

2. Какие сущности вы выделите и какую роль они будут играть?
    
3. Как можно обновлять актуальное состояние заказов без использования `updated_at`?
    
4. Как можно оптимизировать работу с данными такого рода?
