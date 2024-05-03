---
бд: 2024-05-03
---
#### Добавление данных
Для добавления данных применяется команда INSERT, которая имеет следующий формальный синтаксис:

```sql
INSERT INTO имя_таблицы (столбец1, столбец2, ... столбецN)
VALUES (значение1, значение2, ... значениеN)
```
Допустим, у нас в базе данных есть следующая таблица:

```sql
CREATE TABLE Products
(
    Id SERIAL PRIMARY KEY,
    ProductName VARCHAR(30) NOT NULL,
    Manufacturer VARCHAR(20) NOT NULL,
    ProductCount INTEGER DEFAULT 0,
    Price NUMERIC
);
```

Добавим в нее одну строку с помощью команды `INSERT`:
```sql
INSERT INTO Products VALUES (1, 'Galaxy S9', 'Samsung', 4, 63000)
```

Стоит учитывать, что значения для столбцов в скобках после ключевого слова `VALUES` передаются по порядку их объявления.

Также при вводе значений можно указать непосредственные столбцы, в которые будут добавляться значения:

```sql
INSERT INTO Products (ProductName, Price, Manufacturer)
VALUES ('iPhone X', 71000, 'Apple');
```

Также мы можем добавить сразу несколько строк:
```sql
INSERT INTO Products  (ProductName, Manufacturer, ProductCount, Price)
VALUES
('iPhone 6', 'Apple', 3, 36000),
('Galaxy S8', 'Samsung', 2, 46000),
('Galaxy S8 Plus', 'Samsung', 1, 56000)
```
#### Возвращение значений
Если мы добавляем значения только для части столбцов, то мы можем не знать, какие значения будут у других столбцов. Например, какое значение получит столбец Id у товара. С помощью оператора `RETURNING` мы можем получить это значение:

```sql
INSERT INTO Products
(ProductName, Manufacturer, ProductCount, Price)
VALUES('Iphone X', 'Apple', 0, 71000) RETURNING id;
```

Добавляет и возвращает ID