Заданиие:
В базе данных MS SQL Server есть продукты и категории. Одному продукту может соответствовать много категорий, в одной категории может быть много продуктов. Напишите SQL запрос для выбора всех пар «Имя продукта – Имя категории». Если у продукта нет категорий, то его имя все равно должно выводиться.

Ответ:
Предположим, у нас есть две таблицы:
1. Products с полями ProductID и ProductName.
2. Categories с полями CategoryID и CategoryName.

Промежуточная таблица ProductCategories, которая связывает продукты с категориями, с полями ProductID и CategoryID

Запрос: 
```
SELECT 
    p.ProductName, 
    c.CategoryName
FROM 
    Products p
LEFT JOIN 
    ProductCategories pc ON p.ProductID = pc.ProductID
LEFT JOIN 
    Categories c ON pc.CategoryID = c.CategoryID
ORDER BY 
    p.ProductName, c.CategoryName;
```
