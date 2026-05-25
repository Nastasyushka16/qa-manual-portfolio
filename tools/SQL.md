| Умение | Что могу делать |
|--------|----------------|
| **SELECT** | Выборка данных |
| **INSERT** | Добавление новых строк в таблицу |
| **CREATE TABLE** | Создание новой таблицы |
| **(INNER) JOIN** | Объединение двух и более таблиц |
| **WHERE** | Фильтрация данных по условиям |
| **ORDER BY** | Сортировка результатов |
| **GROUP BY** | Группировка данных |
| **Агрегатные функции** | COUNT, SUM, AVG, MIN, MAX |

## 1. Создание таблицы

CREATE TABLE users (
    users_id INT PRIMARY KEY,
    name VARCHAR(100),
    email VARCHAR(100),
    age INT
);

CREATE TABLE orders (
    orders_id INT PRIMARY KEY,
    user_id INT,
    order_date DATE,
    summa DECIMAL(10,2)
);

## 2. Добавление данных

INSERT INTO users (users_id, name, email, age)
VALUES 
    (1, 'Лев', 'lev@gmail.com', 18),
    (2, 'Иван', 'ivan@gmail.com', 50),
    (3, 'Маня', 'manya@gmail.com', 22);

INSERT INTO orders (orders_id, user_id, order_date, summa)
VALUES
    (1, 1, '2025-01-15', 1500.00),
    (2, 2, '2025-01-20', 800.00),
    (3, 2, '2025-02-25', 1200.00);

## 3. Выборка с фильтрацией и сортировкой

SELECT name, email, age 
FROM users
WHERE age > 18
ORDER BY age DESC;

SELECT DISTINCT *
FROM orders;

## 4. GROUP BY

SELECT age, COUNT(*) AS user_count
FROM users
GROUP BY age;

## 5. JOIN

SELECT name, SUM(summa) AS сумма_заказов
FROM users
INNER JOIN orders ON users.users_id = orders.user_id
GROUP BY name;
