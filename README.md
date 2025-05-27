# SQL
1) Выберите из таблицы orders все заказы
![image](https://github.com/user-attachments/assets/8ada50b3-27cc-4880-8375-b4333ccaac6f)
Ответ: Select * from orders;
2) Выберите из таблицы orders все заказы кроме новых. У новых заказов status равен "new". Использовать in
   ![image](https://github.com/user-attachments/assets/4fd42d61-dd96-4e4c-be78-ffb7df2c3b9c)
Ответ: Select * from orders where status in ('delivery', 'in_progress', 'cancelled');
3) Выберите из таблицы orders все новые и отмененные заказы. У отмененных заказов status равен "cancelled". У новых заказов status равен "new".
   ![image](https://github.com/user-attachments/assets/d2d5896b-9e99-43be-a529-83de1dc5d0dc)
Ответ: Select * from orders where status in ('new', 'cancelled');
4) Выберите из таблицы orders все заказы содержащие более 3 товаров (products_count).
Вывести нужно только номер (id) и сумму (sum) заказа.
![image](https://github.com/user-attachments/assets/5f857bb7-f290-430a-be61-ee01be7d0b3b)
Ответ: Select id, sum from orders where products_count>3;



1) Выберите из таблицы orders 3 самых дешевых заказа за всё время.
Данные нужно отсортировать в порядке убывания цены.
Отмененные заказы не учитывайте.
![image](https://github.com/user-attachments/assets/5b8d2fdc-2518-4886-801e-e28cc925fab9)
![image](https://github.com/user-attachments/assets/9c3ccef8-ca0f-4c33-a0d9-33b96bcafac1)
Ответ: SELECT * FROM orders WHERE status != 'cancelled' ORDER BY sum ASC LIMIT 3;
2) Выберите из таблицы orders 2 самых дорогих заказов за всё время.
Данные нужно отсортировать в порядке убывания цены.
Отмененные заказы не учитывайте.
![image](https://github.com/user-attachments/assets/8340c706-2791-4084-bc4a-701a1416626f)
![image](https://github.com/user-attachments/assets/cf35d6b9-7ea0-41a8-857c-d7ed46ec49b8)
Ответ: SELECT * FROM orders WHERE status != 'cancelled' ORDER BY sum DESC LIMIT 2;
3) Добавьте в таблицу orders данные о новом заказе стоимостью 8000 рублей. В заказе 4 товара (products).
![image](https://github.com/user-attachments/assets/dfee366e-9f25-4582-a098-424e8bf9bb46)
![image](https://github.com/user-attachments/assets/7dd73fab-618d-4fef-ac54-496b68eab3be)
Ответ: INSERT INTO orders (id, products, sum) VALUES (6, 4, 8000);
4) Добавьте в таблицу products новый товар — «VR-очки», стоимостью 70000 рублей в количестве (count) 2 штук.
![image](https://github.com/user-attachments/assets/5aa26f90-2514-4b8a-b0cd-2b586cb123ee)
![image](https://github.com/user-attachments/assets/5c67f61b-ed24-4027-b5c4-6ac64a682640)
Ответ: INSERT INTO products (id, name, count, price) VALUES (7, 'VR-очки', 2, 70000);
5) В таблицу products внесли данные с ошибкой, вместо "PS5" в наименовании написали IMAC. Исправьте ошибку.
![image](https://github.com/user-attachments/assets/c79e7851-8ce7-4039-9ca0-e4a460492395)
![image](https://github.com/user-attachments/assets/d36dd19a-c7f5-4a63-8a59-c0d785596307)
Ответ: UPDATE products SET name = 'PS5' WHERE name = 'IMAC';

Создайте таблицу users с полем id типа INT и двумя текстовыми полями, которые будут хранить имя (first_name) и фамилию (last_name). Длина имени и фамилии не превышает 50 символов.
Добавьте в таблицу трех пользователей: Дмитрия Иванова, Анатолия Белого и Дениса Давыдова.
![image](https://github.com/user-attachments/assets/856b6562-190f-4631-9f65-88fd9ebdb9ab)
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(50),
    last_name VARCHAR(50)
);
![image](https://github.com/user-attachments/assets/aa82cfe9-7909-4449-a737-a1e568623135)
INSERT INTO users (first_name, last_name)
VALUES
    ('Дмитрий', 'Иванов'),
    ('Анатолий', 'Белый'),
    ('Денис', 'Давыдов');
![image](https://github.com/user-attachments/assets/dbe5ee16-20e4-43cc-851e-7b5f1da2dd52)


![image](https://github.com/user-attachments/assets/92f9ebc4-974e-474c-9682-c77459656878)


1) Создайте таблицу users для хранения информации о пользователях сайта.
В таблице должны быть следующие поля:

id – идентификатор, целое положительное;
email – адрес электронной почты, строка не более 100 символов;
date_joined – дата регистрации (достаточно хранить дату, без времени)
last_activity – дата и время последней активности (с точностью до секунд).

НЕВЕРНОЕ РЕШЕНИЕ(Ошибка в повторении действия):
CREATE TABLE users(
id INT UNSIGNED,
email VARCHAR(100),
date_joined DATE,
last_activity DATETIME
);

INSERT INTO users (id, email, date_joined, last_activity)
VALUES (1, "user1@domain.com", "2014-12-12", "2016-04-08 12:34:54")
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (2, "user2@domain.com", "2014-12-12", "2017-02-13 11:46:53")
INSERT INTO users (id, email, date_joined, last_activity)
VALUES (3, "user3@domain.com", "2014-12-13", "2017-04-04 05:12:07")

ВЕРНОЕ РЕШЕНИЕ:
DROP TABLE IF EXISTS users;

CREATE TABLE users (
    id INT UNSIGNED,
    email VARCHAR(100),
    date_joined DATE,
    last_activity DATETIME
);

INSERT INTO users (id, email, date_joined, last_activity)
VALUES
(1, 'user1@domain.com', '2014-12-12', '2016-04-08 12:34:54'),
(2, 'user2@domain.com', '2014-12-12', '2017-02-13 11:46:53'),
(3, 'user3@domain.com', '2014-12-13', '2017-04-04 05:12:07');

![image](https://github.com/user-attachments/assets/1b1698ac-1df6-4c30-8e1a-94203c8cd2b2)

2) Создайте таблицу calendar для хранения календаря посетителей.
В таблице должны быть следующие поля:

id – идентификатор записи в календаре, целое положительное;
user_id – идентификатор пользователя, целое положительное;
doctor_id – идентификатор доктора, целое положительное;
visit_date – дата и время визита (точность до секунд).

НЕВЕРНОЕ РЕШЕНИЕ(Ошибка: Отсутствие первичного ключа (PRIMARY KEY) с автоинкрементом (AUTO_INCREMENT) для поля id в таблице calendar приводит к дублированию записей и невозможности гарантировать уникальность идентификаторов):
Create table calendar (
id int unsigned,
user_id int unsigned,
doctor_id int unsigned,
visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date)
Values (1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),
(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 4641, 2,'2017-04-09 09:00:00'),
(5, 15, 2,'2017-04-09 10:00:00')

ВЕРНОЕ РЕШЕНИЕ:
Create table calendar (
id int unsigned,
user_id int unsigned,
doctor_id int unsigned,
visit_date datetime);
Insert into calendar (id, user_id, doctor_id, visit_date)
Values 
(1, 1914 , 1, '2017-04-08 12:00:00'),
(2, 12, 1, '2017-04-08 12:30:00'),
(3, 4641, 2, '2017-04-09 09:00:00'),
(4, 784, 1,'2017-04-08 13:00:00'),
(5, 15, 2,'2017-04-09 10:00:00')

![image](https://github.com/user-attachments/assets/2ca1a2c4-db77-49c8-b9a2-fde03cc1cfc0)

3) Создайте таблицу users , в которой будут следующие поля:

id — идентификатор, целые положительные числа.
first_name— имя, строки до 50 символов.
last_name — фамилия, строки до 60 символов.
bio — биография, текст до 65000 символов.

НЕВЕРНОЕ РЕШЕНИЕ(Некорректное использование атрибута unsigned для строковых полей (first_name, last_name), так как он применим только к числовым типам данных): 
create table users (
id int (10) unsigned,
first_name varchar (50) unsigned,
last_name varchar (60) unsigned,
bio text
);
INSERT INTO users (id, first_name, last_name, bio)
VALUES
(1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''),
(3,'Дмитрий','Соколов','Профессиональный программист.')

ВЕРНОЕ РЕШЕНИЕ:
DROP TABLE if EXISTS users;

create table users (
id int (10) unsigned,
first_name varchar (50),
last_name varchar (60),
bio text
);
INSERT INTO users (id, first_name, last_name, bio)
VALUES
(1,'Антон','Кулик','С отличием окончил 39 лицей.'),
(2,'Сергей','Давыдов',''),
(3,'Дмитрий','Соколов','Профессиональный программист.')

![image](https://github.com/user-attachments/assets/e788e186-407f-401a-9a11-79514cecdf8f)

1) Выберите из таблицы orders 4 самых дорогих заказов за всё время.
Данные нужно отсортировать в порядке убывания цены.
Отмененные заказы не учитывайте.
![image](https://github.com/user-attachments/assets/acb97f7c-fef4-41f3-af1f-70408f40d684)

ОТВЕТ: 
SELECT *
FROM orders
WHERE status != 'cancelled'  
ORDER BY sum DESC
LIMIT 4;

2) Выберите из таблицы products название и цены четырех самых дешевых товаров, которые есть на складе.
![image](https://github.com/user-attachments/assets/1fa24b47-ba2b-43b3-bc67-69882881d632)

ОТВЕТ:
SELECT name, price
FROM products
WHERE count > 0  
ORDER BY price ASC 
LIMIT 4;

3)Выберите из таблицы orders три последних заказа (по дате date) стоимостью от 3200 рублей и выше.
Данные отсортируйте по дате в обратном порядке.
![image](https://github.com/user-attachments/assets/1afd5854-b948-4cee-a3b3-902596a34a7a)

ОТВЕТ:
SELECT *
FROM orders
WHERE 
    sum >= 3200          
    AND date IS NOT NULL 
ORDER BY date DESC
LIMIT 3;

4) Создайте данную таблицу:
![image](https://github.com/user-attachments/assets/13912e9f-3479-4aef-b178-cfda9c1bc430)

ОТВЕТ:
DROP TABLE If EXISTS products;
CREATE TABLE products (
    id INT PRIMARY KEY,
    name VARCHAR(100),
    count INT,
    price INT
);


INSERT INTO products (id, name, count, price) VALUES
(1, 'Стиральная машина', 5, 10000),
(2, 'Холодильник', 0, 10000),
(3, 'Микроволновка', 3, 4000),
(4, 'Пылесос', 2, 4500),
(5, 'Вентилятор', 0, 700),
(6, 'Телевизор', 7, 31740),
(7, 'Тостер', 2, 2500),
(8, 'Принтер', 4, 3000),
(9, 'Активные колонки', 1, 2900),
(10, 'Ноутбук', 4, 36990),
(11, 'Посудомоечная машина', 0, 17800),
(12, 'Видеорегистратор', 23, 4000),
(13, 'Смартфон', 8, 12300),
(14, 'Флешка', 4, 1400),
(15, 'Блендер', 0, 5500),
(16, 'Газовая плита', 5, 11900),
(17, 'Клавиатура', 3, 1800);

![image](https://github.com/user-attachments/assets/5cf4708f-4379-4ce2-b321-69dda5579a2c)


5) Из этой таблицы сделать выборку на основе задания: Сайт выводит товары по 5 штук. Выберите из таблицы products товары, которые пользователи увидят на 3 странице каталога при сортировке в порядке возрастания цены (price).
![image](https://github.com/user-attachments/assets/d4a30508-54df-47f4-a23b-1540b9ac8c1d)

ОТВЕТ: 
SELECT *
FROM products
ORDER BY price ASC, id ASC
LIMIT 5 OFFSET 10;



1) Создайте таблицу orders для хранения списка заказов:

id — идентификатор, целое положительное.
user_id — идентификатор пользователя, который оформил заказ. Целое положительное, NULL запрещен.
amount — стоимость заказа. Целое положительное число не более 1 млн. NULL запрещен, по умолчанию 0.
created — дата и время создания заказа. NULL запрещен.
state — статус заказа. Выбор из new, cancelled, in_progress, delivered, completed. Можно выбрать только один вариант. NULL запрещен. По умолчанию должен стоять new.
Добавьте 3 записи так, чтобы получалась таблица ниже:
![image](https://github.com/user-attachments/assets/7c263751-8efe-4f7f-bcb6-65b878a0abb9)

ОТВЕТ:
DROP TABLE If EXISTS orders; 
CREATE TABLE orders (
    id INT AUTO_INCREMENT PRIMARY KEY,
    user_id INT NOT NULL,
    amount INT NOT NULL CHECK (amount BETWEEN 0 AND 1000000) DEFAULT 0,
    created DATETIME NOT NULL,
    state ENUM('new', 'cancelled', 'in_progress', 'delivered', 'completed') NOT NULL DEFAULT 'new'
);


INSERT INTO orders (user_id, amount, created, state) VALUES
(56, 5400, '2018-02-01 17:46:59', 'new'),
(90, 249, '2018-02-01 19:13:04', 'new'),
(78, 2200, '2018-02-01 22:43:09', 'new');

![image](https://github.com/user-attachments/assets/c729f336-4c09-4ead-84f3-371a868bf0b1)


2) Создайте таблицу users для хранения списка пользователей сайта:

id — идентификатор, целое положительное.
first_name — имя, строка до 20 символов. NULL запрещен.
last_name — фамилия, строка до 20 символов. NULL запрещен.
patronymic — отчество, строка до 20 символов. NULL запрещен, по умолчанию пустая строка.
is_active — отметка об активности пользователя. Логическое поле, по умолчанию TRUE.
is_superuser — отметка администратора. Логическое поле, по умолчанию FALSE.
Добавьте 3 записи так, чтобы получалась таблица ниже:
![image](https://github.com/user-attachments/assets/dcdf2848-4adb-4f9c-9790-f9686710cec6)

ОТВЕТ:
DROP TABLE If EXISTS users; 

CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    first_name VARCHAR(20) NOT NULL,
    last_name VARCHAR(20) NOT NULL,
    patronymic VARCHAR(20) NOT NULL DEFAULT '',
    is_active ENUM('TRUE', 'FALSE') NOT NULL DEFAULT 'TRUE',
    is_superuser ENUM('TRUE', 'FALSE') NOT NULL DEFAULT 'FALSE'
);


INSERT INTO users (first_name, last_name, patronymic, is_active, is_superuser) VALUES
('Дмитрий', 'Иванов', '', 'TRUE', 'FALSE'),
('Анатолий', 'Белый', 'Сергеевич', 'TRUE', 'TRUE'),
('Андрей', 'Крючков', '', 'FALSE', 'FALSE');

![image](https://github.com/user-attachments/assets/1c4ecd65-6b2c-4ab4-b1c9-b18e0636de7a)

3) Создайте таблицу products для хранения товаров в интернет магазине:

id — идентификатор, целое положительное.
category_id — категория, целое положительное. Может принимать NULL. По умолчанию NULL.
name — название, строка до 100 символов. NULL запрещен.
count — количество, целое положительное до 255. NULL запрещен, по умолчанию 0.
price — цена типа DECIMAL с 10 знаками, 2 из которых выделены для копеек. NULL запрещен, по умолчанию 0.00.
Добавьте 3 записи так, чтобы получалась таблица ниже:
![image](https://github.com/user-attachments/assets/27904cba-7d06-40bf-a883-ffe27ae08df8)

ОТВЕТ:
DROP TABLE If EXISTS products;
CREATE TABLE products (
    id INT AUTO_INCREMENT PRIMARY KEY,
    category_id INT UNSIGNED DEFAULT NULL,
    name VARCHAR(100) NOT NULL,
    count TINYINT UNSIGNED NOT NULL DEFAULT 0,
    price DECIMAL(10, 2) NOT NULL DEFAULT 0.00
);


INSERT INTO products (id, category_id, name, count, price) VALUES
(1, 1, 'Кружка', 5, 45.90),
(2, 17, 'Фломастеры', 0, 78.00),
(3, NULL, 'Сникерс', 12, 50.80);

![image](https://github.com/user-attachments/assets/53a45227-949f-4025-89ad-2d7983b36ee1)
