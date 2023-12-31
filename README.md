# **Шпаргалка по MySql**

# **Настройка консоли**
1. `\sql` - переключиться на язык `SQL`;
2. `\connect root@localhost:3306` - подключение к локальному серверу;

# **Создание и удаление БД**
* `show databases;` - просмотр созданных БД;
* `CREATE DATABASE <имя_БД>;` - cоздание БД;
* `drop database <имя_БД>;` - удаление БД;
* `use <имя_БД>;` - установить БД в качестве текущей;

# **Основаные типы данных**
* `INT` - Целое число, могут принимать значения
от -2 147 483 648 до 2 147 483 647;
* `DECIMAL`/`NUMERIC` (эквевалентны) - Вещественное число,
в скобках указывается максимальная
длина числа (включает символы слева и справа от десятичной запятой)
и количество знаков после запятой;
* `DATE` - Дата в формате ГГГГ-ММ-ДД;
* `VARCHAR` - Строка длиной не более 65 535 символов,
в скобках указывается максимальная
длина строки, которая может храниться в поле;
* `INT PRIMARY KEY AUTO_INCREMENT` - тип ключевого столбца;

# **Создание таблицы и удаление таблицы**
* Создание:
  ```
  CREATE TABLE <имя_таблицы>(
      genre_id INT PRIMARY KEY AUTO_INCREMENT, 
      name_genre VARCHAR(30)
  );
  ```
* Удаление: `drop table <имя_таблицы>;`.

# **Вставка записи в таблицу**
```
INSERT INTO таблица(поле1, поле2)
VALUES (значение1, значение2),
	   (значение3, значение4);
```

# **Выборка данных (SELECT)**
* `SELECT * FROM book;` - Выбрать все записи таблицы `book`;
* `SELECT title, amount FROM book;` - Выбрать названия книг и их количества из таблицы `book`;
* `SELECT title AS Название, amount FROM book;` - Выбрать все названия книг и их количества из таблицы `book` , для столбца `title` задать новое имя `Название`;
* `SELECT title, author, price, amount, price * amount AS total FROM book;` - Вывести всю информацию о книгах, а также для каждой позиции посчитать ее стоимость (произведение цены на количество). Вычисляемому столбцу дать имя `total`;
* `IF(логическое_выражение, выражение_1, выражение_2)`:
    ```sql
    SELECT title, amount, price, 
        IF(amount<4, price*0.5, price*0.7) AS sale
    FROM book;
    ```
    Для каждой книги из таблицы book установим скидку следующим образом: если количество книг меньше 4, то скидка будет составлять 50% от цены, в противном случае 30%.
* Выборка данных по условию:
    ```sql
    SELECT title, price 
    FROM book
    WHERE price < 600;
    ```
    Вывести название и цену тех книг, цены которых меньше 600 рублей;
* `WHERE amount BETWEEN 5 AND 14;` - аналог `WHERE 5 <= amount <= 14`;
* `WHERE author IN ('Булгаков М.А.', 'Достоевский Ф.М.');` - аналог `WHERE author = 'Булгаков М.А.' OR author = 'Достоевский Ф.М.';`;
* Сортировка:
    ```sql
    SELECT author, title
    FROM book
    WHERE amount BETWEEN 2 AND 14
    ORDER BY author DESC, title;
    ```

# Оператор `LIKE`
* `%` - Любая строка, содержащая ноль или более символов;
Например:
    ```sql
    SELECT * FROM book WHERE author LIKE '%М.%'
    ```
    ```
    выполняет поиск и выдает все книги, инициалы авторов которых содержат «М.»
    ```
* `_` - Любой одиночный символ;
Например:
    ```sql
    SELECT * FROM book WHERE title LIKE 'Поэм_'
    ```
    ```
    выполняет поиск и выдает все книги, названия которых либо «Поэма», либо «Поэмы» и пр.
    ```