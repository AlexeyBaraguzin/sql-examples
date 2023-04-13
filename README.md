# SQL

Несколько примеров решенных мной заданий на курсе ["Интерактивный тренажер по SQL"](https://stepik.org/course/63054) на платформе Stepik.

## Запросы для нескольких таблиц с группировкой (Left Join)

Посчитать количество экземпляров книг каждого автора из таблицы author. Вывести тех авторов, количество книг которых меньше 10, в отсортированном по возрастанию количества виде. Последний столбец назвать Количество.

### Логическая схема базы данных:

![LSBD](https://github.com/AlexeyBaraguzin/sql-examples/blob/main/assets/left_join_lsbd.jpg)

### Структура и наполнение таблиц

![SNT](https://github.com/AlexeyBaraguzin/sql-examples/blob/main/assets/left_join_snt.jpg)

### SQL запрос

```SQL
SELECT name_author, SUM(amount) AS Количество
FROM author
    LEFT JOIN book
    ON author.author_id = book. author_id
GROUP BY name_author
HAVING SUM(amount)<10 OR COUNT(title) = 0
ORDER BY Количество;
```

## Вложенный запрос, оператор IN

Вывести информацию (автора, книгу и количество) о тех книгах, количество экземпляров которых в таблице book не дублируется.

### Структура и наполнение таблицы book

![SNT](https://github.com/AlexeyBaraguzin/sql-examples/blob/main/assets/in_snt.jpg)

### SQL запрос

```SQL
SELECT author, title, amount
FROM book
WHERE amount IN (
        SELECT amount
        FROM book
        GROUP BY amount
        HAVING COUNT(amount)=1
      );
```
