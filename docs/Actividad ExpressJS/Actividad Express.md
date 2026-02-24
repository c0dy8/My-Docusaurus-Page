# 📘 API de Ejercicios SQL con Express y MySQL


## 📌 Descripción

- Este proyecto consiste en una API REST desarrollada con Node.js, Express y MySQL2, donde se practican consultas SQL avanzadas utilizando:

- INNER JOIN

- GROUP BY

- SUM()

- COUNT()

- AVG()

- DISTINCT

- ORDER BY

- Cada ejercicio está expuesto como un endpoint independiente.

## 🛠 Tecnologías Utilizadas

- Node.js

- Express

- MySQL2

- MySQL

## ⚙ Instalación

```bash 
npm install express mysql2
```
## 🚀 Ejecutar el servidor
```bash 
node server.js
```

### Servidor disponible en:

```bash 
http://localhost:3000
```

### 📂 Código Completo del Servidor

```JS 
const express = require('express');
const mysql = require('mysql2');

const app = express();
app.use(express.json());

// Crear conexión
const connection = mysql.createConnection({
    host: '157.180.40.190',
    user: 'root',
    password: 'scORHWprCvp26Gz1zwPQgSsokHyPC2',
    database: 'db_andrescortes_ejercicio'
});

// Conectar
connection.connect((err) => {
    if (err) {
        console.error('Error de conexión:', err);
        return;
    }
    console.log('Conectado a la base de datos');
});
```

## 🧠 Ejercicios Nivel 1
### Obtener nombre, email y número de pedido de un usuario específico (ID = 3)

```JS 
app.get('/level1/ejercicio-1', (req, res) => {

    const sql = 'SELECT users.name, users.email, orders.order_number FROM users INNER JOIN orders ON users.id = orders.user_id WHERE users.id = 3;';

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 2
### Obtener pedidos de un usuario por su email

```JS 
app.get('/level1/ejercicio-2', (req, res) => {

    const sql = `SELECT o.id AS codigo_pedido, o.created_at AS fecha FROM orders o INNER JOIN users u ON o.user_id = u.id WHERE u.email = 'ponce.luisa@santos.org';`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 3
### Listar productos junto con su categoría

```JS 
app.get('/level1/ejercicio-3', (req, res) => {

    const sql = `SELECT products.name AS product_name, categories.name AS category_name FROM products INNER JOIN categories ON products.category_id = categories.id;`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 4
### Consulta similar al ejercicio 3

```JS 
app.get('/level1/ejercicio-4', (req, res) => {

    const sql = `SELECT products.name AS product_name, categories.name AS category_name FROM products INNER JOIN categories ON products.category_id = categories.id;`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 5
### Calcular el total gastado por un usuario específico

```JS 
app.get('/level1/ejercicio-5', (req, res) => {

    const sql = `SELECT users.name,SUM(orders.total) AS total_gastado FROM users INNER JOIN orders ON users.id = orders.user_id WHERE users.id = 3 GROUP BY users.name;`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 6
### Contar pedidos agrupados por estado

```JS 
app.get('/level1/ejercicio-5', (req, res) => {

    const sql = `SELECT users.name,SUM(orders.total) AS total_gastado FROM users INNER JOIN orders ON users.id = orders.user_id WHERE users.id = 3 GROUP BY users.name;`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 7
###  Productos de la categoría "ropa y moda" ordenados por precio descendente

```JS 
app.get('/level1/ejercicio-7', (req, res) => {

    const sql = `SELECT products.name, products.sale_price FROM products INNER JOIN categories ON products.category_id = categories.id WHERE categories.name = 'ropa y moda' ORDER BY products.sale_price DESC;`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```
## 🔹 Ejercicio 8
### Productos y cantidades de un pedido específico

```JS 
app.get('/level1/ejercicio-8', (req, res) => {

    const sql = `SELECT order_product.product_id, order_product.quantity FROM order_product INNER JOIN orders ON order_product.order_id = orders.id WHERE orders.order_number = 'ORD-2026-S2EOKP';`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 9
### Usuarios únicos que han realizado pedidos en una ciudad específica

```JS 
app.get('/level1/ejercicio-9', (req, res) => {

    const sql = `SELECT DISTINCT users.name, users.last_name, users.email FROM users INNER JOIN orders ON users.id = orders.user_id WHERE users.city = 'Villa Navarro';`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 10
### Promedio del total de pedidos por usuario

```JS 
app.get('/level1/ejercicio-10', (req, res) => {

    const sql = `SELECT users.name, AVG(orders.total) AS promedio_pedidos FROM users INNER JOIN orders ON users.id = orders.user_id GROUP BY users.name;`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

# 🧠 Ejercicios Nivel 2

## 🔹 Ejercicio 11
### Listar pedidos con sus productos y precios

```JS 
app.get('/level-2/ejercicio-11', (req, res) => {

    const sql = `SELECT orders.order_number, orders.order_date, products.name AS producto,products.sale_price AS precio_venta FROM orders INNER JOIN order_product ON orders.id = order_product.order_id INNER JOIN products ON order_product.product_id = products.id ORDER BY orders.order_number, products.name;`;

    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

## 🔹 Ejercicio 12
### Calcular el ingreso total por categoría

```JS 
app.get('/level-2/ejercicio-12', (req, res) => {

    const sql = `SELECT c.name AS categoria, SUM(p.sale_price * op.quantity) AS ingreso_total FROM categories c INNER JOIN products p ON c.id = p.category_id INNER JOIN order_product op ON p.id = op.product_id GROUP BY c.name ORDER BY ingreso_total DESC;`
    
    connection.query(sql, (err, results) => {

        if (err) {
            console.error('Error en la consulta:', err);
            return res.status(500).json({ error: 'Error en la consulta' });
        }

        res.json(results);
    });
});
```

# ▶ Inicio del Servidor

```JS 
app.listen(3000, () => {
    console.log('Servidor corriendo en http://localhost:3000');
});
```