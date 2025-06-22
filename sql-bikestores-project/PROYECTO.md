# 📊 Análisis de Datos con SQL | Tienda de Bicicletas

Este proyecto demuestra mi habilidad para extraer información valiosa y realizar análisis de datos utilizando SQL en una base de datos existente de una tienda de bicicletas. El enfoque principal está en responder preguntas de negocio clave a través de consultas SQL bien elaboradas, mostrando competencia en la recuperación, agregación y manipulación de datos.

---

## 🎯 Objetivo del Proyecto

-   **Análisis de Datos:** Extraer información relevante y responder a preguntas de negocio específicas utilizando consultas SQL.
-   **Generación de Insights:** Identificar tendencias, patrones de ventas, rendimiento de productos y clientes clave a partir de los datos.
-   **Dominio de SQL:** Demostrar habilidades avanzadas en la escritura de consultas SQL para el análisis de datos complejos.
-   **Comprensión de Bases de Datos:** Navegar y comprender la estructura de una base de datos relacional existente para realizar análisis efectivos.

---

## 🧱 Estructura de la Base de Datos (Base para el Análisis)

Para la realización de este análisis, se utilizó una base de datos relacional de una tienda de bicicletas. A continuación, se presenta el diagrama Entidad-Relación (ERD) que ilustra la estructura y las relaciones entre las tablas de esta base de datos, sirviendo como referencia para las consultas realizadas:

### Diagrama Entidad-Relación (ERD)

![image](https://github.com/user-attachments/assets/7fb74c3a-fc13-4072-a41d-33e72de89597)

---

## 📄 Tablas Analizadas

Las consultas se ejecutaron sobre las siguientes tablas principales de la base de datos:

-   **`brands`**: Contiene información sobre las marcas de los productos.
-   **`categories`**: Permite clasificar los productos.
-   **`products`**: Almacena los detalles de todos los productos (bicicletas, componentes, etc.).
-   **`stocks`**: Controla el inventario de productos en cada sucursal.
-   **`customers`**: Contiene los datos de los clientes.
-   **`stores`**: Gestiona la información de las diferentes sucursales de la tienda.
-   **`orders`**: Registra los pedidos realizados.
-   **`order_items`**: Detalla los productos incluidos en cada pedido.
-   **`staffs`**: Contiene información sobre el personal de ventas.

---

## 🔍 Consultas SQL Clave

Esta sección presenta una serie de consultas SQL desarrolladas para analizar diferentes aspectos del negocio de la tienda de bicicletas y extraer insights valiosos:

### Análisis de Ventas y Productos

#### 1. Top 5 de productos más vendidos
![image](https://github.com/user-attachments/assets/8c70c8e7-98ff-4c65-8eaa-29817e172eea)

```sql
SELECT *
FROM production.products;

SELECT * 
FROM sales.order_items;


SELECT TOP 5 p.product_name, SUM(oi.quantity) AS total_quantity
FROM sales.order_items AS oi
INNER JOIN production.products AS p
ON oi.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_quantity DESC
```

#### 2. Bottom 5 de productos menos vendidos
![image](https://github.com/user-attachments/assets/64b833b4-9990-4b9b-9e0c-60bc4a50e361)

```sql
SELECT TOP 5 p.product_name, SUM(oi.quantity) AS total_quantity
FROM sales.order_items AS oi
INNER JOIN production.products AS p
ON oi.product_id = p.product_id
GROUP BY p.product_name
ORDER BY total_quantity ASC
```

#### 3. Top 5 de categorías de productos que más ingresos generan 
![image](https://github.com/user-attachments/assets/aa1768b7-a046-44de-9a14-19d7df9e2b65)

```sql
SELECT * 
FROM production.categories


SELECT TOP 5 c.category_name, CAST(ROUND(SUM(list_price),0) AS INT) AS total_sales
FROM sales.order_items AS oi
INNER JOIN production.categories AS c
ON oi.product_id = c.category_id
GROUP BY c.category_name
ORDER BY total_sales DESC
```

#### 4. ¿Qué tiendas tienen el mayor número de órdenes?
![image](https://github.com/user-attachments/assets/f02da8c0-fdb8-4ee5-b8e2-5fe3d6617f4d)

```sql
SELECT s.store_name, COUNT(o.order_id) AS number_of_orders
FROM sales.stores as s
INNER JOIN sales.orders as o
ON  s.store_id = o.store_id 
GROUP BY s.store_name
ORDER BY number_of_orders DESC
```

#### 5. ¿Cuál es el promedio de cantidad de productos por orden?
![image](https://github.com/user-attachments/assets/360e11f3-e8c8-4520-bf74-8a2b58272fbd)

```sql
SELECT *
FROM sales.order_items


SELECT AVG(total_quantity) AS avg_quantity_per_order
FROM ( 
SELECT order_id, SUM(quantity) AS total_quantity
FROM sales.order_items
GROUP BY order_id
) AS subquery;
```

#### 6. Top 5 clientes que más han gastado
![image](https://github.com/user-attachments/assets/f67294a0-670e-40b0-ab32-858383f43744)

```sql
SELECT *
FROM sales.customers

SELECT TOP 5 cu.customer_id, cu.first_name, cu.last_name, CAST(ROUND(SUM(oi.quantity * oi.list_price * (1 - oi.discount)),0) AS INT) AS total_spent
FROM sales.customers AS cu
INNER JOIN sales.orders AS o ON cu.customer_id = o.customer_id
INNER JOIN sales.order_items oi ON o.order_id = oi.order_id
GROUP BY cu.customer_id, cu.first_name, cu.last_name
ORDER BY total_spent DESC;
```

#### 7. ¿Cuáles son las marcas de bicicletas más populares en la cantidad de productos vendidos?
![image](https://github.com/user-attachments/assets/c895d28e-d293-49c9-a223-2f525376d7f2)

```sql
SELECT *
FROM production.brands


SELECT b.brand_name, SUM(oi.quantity) AS total_quantity
FROM production.brands AS b
INNER JOIN production.products AS p ON b.brand_id = p.brand_id
INNER JOIN sales.order_items AS oi ON p.product_id = oi.product_id
GROUP BY brand_name
ORDER BY total_quantity DESC
```

#### 8. ¿Cuál es la tendencia de ventas mes a mes?
![image](https://github.com/user-attachments/assets/a73a9ba2-401f-4283-9df9-2b7f63450282)

```sql
SELECT * 
FROM sales.orders;


SELECT YEAR(o.order_date) AS order_year, MONTH(o.order_date) AS order_month, COUNT(*) AS number_of_orders
FROM sales.orders AS o
GROUP BY YEAR(o.order_date), MONTH(o.order_date)
ORDER BY order_year, order_month
```

#### 9. ¿Cuáles son los productos que nunca se han vendido?
![image](https://github.com/user-attachments/assets/b14f6ab1-e19e-4351-8461-cd1f1046a8f3)

```sql
SELECT p.product_id, p.product_name
FROM production.products AS p
LEFT JOIN sales.order_items AS oi
ON p.product_id = oi.product_id
WHERE oi.product_id IS NULL
```

#### 10. ¿Qué staff ha realizado el mayor número de ventas?
![image](https://github.com/user-attachments/assets/ca0f8436-6fa5-436b-8a35-71bb839a0781)

```sql
SELECT *
FROM sales.staffs

SELECT * 
FROM sales.orders;


SELECT CONCAT(first_name,' ', last_name) AS staff_name, COUNT(o.order_id) AS total_sales
FROM sales.staffs AS s
INNER JOIN sales.orders AS o
ON s.staff_id = o.staff_id
GROUP BY CONCAT(first_name,' ', last_name) 
ORDER BY total_sales DESC
```

#### 11. ¿Cuál es el valor promedio de una orden?
![image](https://github.com/user-attachments/assets/a859524c-a58a-41ab-b032-650490e9259d)

```sql
SELECT * 
FROM sales.orders

SELECT *
FROM sales.order_items

SELECT AVG(total_order_price) AS average_order_value
FROM(
SELECT o.order_id, CAST(ROUND(SUM(oi.list_price * oi.quantity * (1 - oi.discount)),0) AS INT) AS total_order_price
FROM sales.orders AS o
INNER JOIN sales.order_items AS oi
ON o.order_id = oi.order_id
GROUP BY o.order_id
) AS order_values
```

#### 12. ¿Qué clientes han realizado compras por encima del promedio en valor?
![image](https://github.com/user-attachments/assets/1d50cd63-5b4d-4c39-969b-87b7f4fbd9e0)

```sql
SELECT * 
FROM sales.orders

SELECT *
FROM sales.customers
  
SELECT cu.customer_id, CONCAT(cu.first_name, ' ', cu.last_name) AS customer_name, CAST(ROUND(SUM(oi.quantity * oi.list_price * (1 - oi.discount)),0) AS INT) AS total_spent
FROM sales.customers AS cu
INNER JOIN sales.orders AS o ON cu.customer_id = o.customer_id
INNER JOIN sales.order_items AS oi ON o.order_id = oi.order_id
GROUP BY cu.customer_id, CONCAT(cu.first_name, ' ', cu.last_name)
HAVING CAST(ROUND(SUM(oi.quantity * oi.list_price * (1 - oi.discount)),0) AS INT) >
    (SELECT AVG(total_order_price) 
	FROM (
	   SELECT CAST(ROUND(SUM(oi.list_price * oi.quantity * (1 - oi.discount)),0) AS INT) AS total_order_price
	   FROM sales.order_items AS oi
	   GROUP BY oi.order_id) AS avg_order_price)
	   ORDER BY total_spent DESC
```

#### 13. ¿Cuántas órdenes se han enviado después de la fecha requerida?
![image](https://github.com/user-attachments/assets/fa86f191-2a34-49a5-ad43-6cc007e711d0)

```sql
SELECT * 
FROM sales.orders

SELECT COUNT(*) AS order_shipped_late
FROM sales.orders
WHERE shipped_date > required_date
```

#### 14. ¿Cuál es el descuento promedio que se ha aplicado a los productos vendidos?
![image](https://github.com/user-attachments/assets/da705f38-8073-4c1d-b7b1-0684f689f971)

```sql
SELECT * 
FROM sales.orders

SELECT COUNT(*) AS order_shipped_late
FROM sales.orders
WHERE shipped_date > required_date
```

#### 15. ¿Cuántas órdenes incluyen productos de múltiples categorías?
![image](https://github.com/user-attachments/assets/f796d022-1572-4ef4-9ba8-801c1e50e2c1)

```sql
SELECT o.order_id, COUNT(DISTINCT p.category_id) AS number_of_categories
FROM sales.orders AS o
INNER JOIN sales.order_items AS oi ON o.order_id = oi.order_id 
INNER JOIN production.products AS p ON oi.product_id = p.product_id
GROUP BY o.order_id
HAVING COUNT(DISTINCT p.category_id) > 1
ORDER BY number_of_categories DESC
```

#### 16. ¿Qué productos tienen un precio de lista significativamente más alto que el promedio de su categoría?
![image](https://github.com/user-attachments/assets/7f88d499-cb55-497e-a4c1-d92e72863fdc)

```sql
SELECT p.product_id, p.product_name, p.list_price, c.category_name, avg_category_price.average_list_price
FROM production.products AS p
INNER JOIN production.categories  AS c ON p.category_id = c.category_id
CROSS APPLY (
    SELECT AVG(list_price) AS average_list_price
    FROM production.products
    WHERE category_id = p.category_id
) AS avg_category_price
WHERE p.list_price > avg_category_price.average_list_price * 1.5
```

#### 17. Relación entre el personal de ventas y el número de órdenes procesadas
![image](https://github.com/user-attachments/assets/763e794b-7e01-42b0-beed-daf3f29ab40b)

```sql
SELECT st.staff_id, CONCAT(st.first_name, ' ', st.last_name) AS staff_name, COUNT(o.order_id) AS number_of_orders
FROM sales.staffs AS st
INNER JOIN sales.orders AS o ON st.staff_id = o.staff_id
GROUP BY st.staff_id, st.first_name, st.last_name
ORDER BY number_of_orders DESC
```

#### 18. Porcentaje de productos vendidos de cada categoría en el último año
![image](https://github.com/user-attachments/assets/b55690a8-daae-451b-842c-3ac0be1b26dc)

```sql
SELECT c.category_id, c.category_name, 
       100.0 * SUM(CASE WHEN YEAR(o.order_date) = YEAR('2017') THEN oi.quantity ELSE 0 END) 
       / NULLIF(SUM(oi.quantity), 0) AS percentage_sold_last_year
FROM production.categories AS c
INNER JOIN production.products AS p ON c.category_id = p.category_id
INNER JOIN sales.order_items AS oi ON p.product_id = oi.product_id
INNER JOIN sales.orders AS o ON oi.order_id = o.order_id
GROUP BY c.category_id, c.category_name
ORDER BY percentage_sold_last_year DESC
```

👤 Autor
Gabriel Rodríguez
LinkedIn
