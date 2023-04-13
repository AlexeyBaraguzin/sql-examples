# SQL

Несколько примеров решенных мной заданий на курсе ["Интерактивный тренажер по SQL"](https://stepik.org/course/63054) на платформе Stepik:

## Left Join

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
