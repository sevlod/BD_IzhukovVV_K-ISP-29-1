    1) Выберите из таблицы orders все заказы:
`SELECT * FROM orders`

![Image](https://github.com/user-attachments/assets/bea8389d-893d-4e47-9876-767e55b095ec)

2) Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in:
`SELECT * FROM orders
WHERE STATUS NOT IN ('new')`

![Image](https://github.com/user-attachments/assets/530b123a-f9b1-439e-b04c-7d883ab00783)

3) Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new":
`SELECT * FROM orders
WHERE STATUS IN ('NEW', 'CANCELLED')`

![Image](https://github.com/user-attachments/assets/f7ffc357-3cca-4672-a91a-106e1b88b049)

4) Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count).
Вывести нужно только номер (id) и сумму (sum) заказа:
```
SELECT id, SUM
FROM orders
WHERE products_count > 3
```

![Image](https://github.com/user-attachments/assets/d2867f5e-6d7f-4b99-80e0-ea6915370131)
