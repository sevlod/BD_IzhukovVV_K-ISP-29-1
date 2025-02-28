# Шпаргалка
🔹 Работа с таблицами:
```
SHOW TABLES;                   # Показать таблицы в текущей БД
DESCRIBE tablename;            # Показать структуру таблицы
CREATE TABLE tablename ( );                              # Создать таблицу
DROP TABLE tablename;           # Удалить таблицу
ALTER TABLE tablename ADD COLUMN email VARCHAR(100);  # Добавить колонку
ALTER TABLE tablename DROP COLUMN email;              # Удалить колонку
TRUNCATE TABLE table_name;                          # Удалить все данные из таблицы
```
🔹 Работа с данными:
```
INSERT INTO tablename (name, age) VALUES ('Ivan', 25);   # Вставить данные
SELECT * FROM tablename;                                 # Вывести все записи
SELECT name, age FROM tablename WHERE age > 20;         # Фильтр
UPDATE tablename SET age = 30 WHERE name = 'Ivan';      # Обновить данные
DELETE FROM tablename WHERE age < 18;                   # Удалить данные

```
🔹 Работа с базами данных:
```
SHOW DATABASES;              # Показать все базы данных
CREATE DATABASE dbname;      # Создать базу данных
USE dbname;                  # Переключиться на базу данных
DROP DATABASE dbname;        # Удалить базу данных

```

# Лабораторная №1

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

# Лабораторная №2
### ЗАДАНИЕ 161 (ДОРОГИЕ ЗАКАЗЫ)

1) Выберите из таблицы orders 3 самых дешевых заказа за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
```
SELECT * 
FROM orders
WHERE status != 'cancelled'
ORDER BY sum ASC
LIMIT 3;
```

![Image](https://i.imgur.com/yAp4RZV.png)

2) Выберите из таблицы orders 2 самых дорогих заказов за всё время. Данные нужно отсортировать в порядке убывания цены. Отмененные заказы не учитывайте.
```
SELECT * 
FROM orders
WHERE status != 'cancelled'
ORDER BY sum DESC
LIMIT 2;
```

![Image](https://i.imgur.com/NPtDk4U.png)

### Задание 166 (Новый заказ)

3) Добавьте в таблицу orders данные о новом заказе стоимостью 8000 рублей. В заказе 4 товара (products).
```
INSERT INTO orders (id, products, sum)
VALUES (6, 4, 8000);
```

![Image](https://i.imgur.com/0bf0tst.png)
Результат:
![Image](https://i.imgur.com/qBlO9Ac.png)

### Задание 167 (Новый товар)

4) Добавьте в таблицу products новый товар — «VR-очки», стоимостью 70000 рублей в количестве (count) 2 штук.
```
INSERT INTO products (id, name, count, price)
VALUES (7, 'VR-очки', 2, 70000);
```

![Image](https://i.imgur.com/UHw0tp4.png)
Результат:
![Image](https://i.imgur.com/xwKzfXM.png)

### Задание 172 (Ошибка в названии товара)

5) В таблицу products внесли данные с ошибкой, вместо "PS5" в наименовании написали IMAC. Исправьте ошибку.
```
UPDATE products
SET name = 'PS5'
WHERE name = 'IMAC';
```

![Image](https://i.imgur.com/QDasNBI.png)
Результат:
![Image](https://i.imgur.com/AUQ1tPq.png)
