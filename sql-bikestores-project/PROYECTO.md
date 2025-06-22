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

![Diagrama de Base de Datos de Tienda de Bicicletas](./diagrama_tienda_bicicletas.png)

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
-   **`staffs`**: (Mencionada en algunas consultas) Contiene información sobre el personal de ventas.

---

## 🔍 Consultas SQL Clave

Esta sección presenta una serie de consultas SQL desarrolladas para analizar diferentes aspectos del negocio de la tienda de bicicletas y extraer insights valiosos:

### Análisis de Ventas y Productos

#### 1. Top 5 de productos más vendidos
![image](https://github.com/user-attachments/assets/8c70c8e7-98ff-4c65-8eaa-29817e172eea)

```sql
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



