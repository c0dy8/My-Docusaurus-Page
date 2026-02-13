---
title: Ejercicios SQL
description: Práctica de consultas SQL organizadas por niveles.
---

# Ejercicios SQL

Colección de ejercicios prácticos utilizando consultas `SELECT`, filtros, operadores lógicos y funciones de agregación en SQL.

---

# Nivel 1 – Consultas Básicas

## Ejercicio 1
Obtener todos los registros de la tabla `users`.

```sql
SELECT * FROM users;
```

## Ejercicio 2
Obtener nombre, apellido y correo electrónico.

```sql
SELECT first_name, last_name, email FROM users;
```

## Ejercicio 3
Obtener todos los usuarios con rol **admin**.

```sql
SELECT * FROM users WHERE role = 'admin';
```

## Ejercicio 4
Obtener usuarios cuyo tipo de documento sea **CC**.

```sql
SELECT * FROM users WHERE document_type = 'CC';
```

## Ejercicio 5
Obtener usuarios nacidos antes del 1 de enero de 2006.

```sql
SELECT * FROM users WHERE birth_date < '2006-01-01';
```

## Ejercicio 6
Obtener usuarios con ingresos mayores a 5.000.000.

```sql
SELECT * FROM users WHERE monthly_income > 5000000;
```

## Ejercicio 7
Obtener usuarios cuyo nombre empiece por la letra "a".

```sql
SELECT * FROM users WHERE first_name LIKE 'a%';
```

## Ejercicio 8
Obtener usuarios que no tengan empresa registrada.

```sql
SELECT * FROM users WHERE company IS NULL;
```

---

# Nivel 2 – Condiciones Combinadas

## Ejercicio 9
Usuarios nacidos antes de 2001 y con rol **employee**.

```sql
SELECT * FROM users 
WHERE birth_date < '2001-01-01' 
AND role = 'employee';
```

## Ejercicio 10
Usuarios con documento **CC** y activos.

```sql
SELECT * FROM users 
WHERE document_type = 'CC' 
AND is_active = 1;
```

## Ejercicio 11
Usuarios nacidos antes de 2006 con rol **user**.

```sql
SELECT * FROM users 
WHERE birth_date < '2006-01-01' 
AND role = 'user';
```

## Ejercicio 12
Empleados con ingresos mayores a 3.000.000.

```sql
SELECT * FROM users 
WHERE role = 'employee' 
AND monthly_income > 3000000;
```

## Ejercicio 13
Usuarios casados con al menos un hijo.

```sql
SELECT * FROM users 
WHERE marital_status = 'Casado' 
AND children_count >= 1;
```

## Ejercicio 14
Usuarios nacidos antes de 1996 o antes de 1986.

```sql
SELECT * FROM users 
WHERE birth_date < '1996-01-01' 
OR birth_date < '1986-01-01';
```

## Ejercicio 15
Admins verificados nacidos antes de 2001.

```sql
SELECT * FROM users 
WHERE role = 'admin' 
AND is_verified = true 
AND birth_date < '2001-01-01';
```

---

# Nivel 3 – Funciones de Agregación

## Ejercicio 16
Contar usuarios agrupados por rol.

```sql
SELECT role, COUNT(role) 
FROM users 
GROUP BY role;
```

## Ejercicio 17
Contar usuarios agrupados por tipo de documento.

```sql
SELECT document_type, COUNT(document_type) 
FROM users 
GROUP BY document_type;
```

## Ejercicio 18
Contar usuarios con rol **user**.

```sql
SELECT COUNT(role) 
FROM users 
WHERE role = 'user';
```

## Ejercicio 19
Promedio de ingresos mensuales.

```sql
SELECT AVG(monthly_income) 
FROM users;
```

## Ejercicio 20
Promedio de ingresos mensuales agrupado por rol.

```sql
SELECT role, AVG(monthly_income) 
FROM users 
GROUP BY role;
```

---

# Conceptos Aplicados

- SELECT
- WHERE
- LIKE
- AND / OR
- IS NULL
- COUNT()
- AVG()
- GROUP BY
