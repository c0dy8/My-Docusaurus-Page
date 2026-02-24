# Vistas y Consultas SQL

## 1 Vista: Usuarios Adultos
### 📌 Descripción
- Crea una vista que muestra usuarios mayores de edad (según la condición establecida en la fecha).

``` sql
CREATE VIEW briam_view_adults_user AS
SELECT
    u.id,
    u.first_name,
    u.last_name,
    u.document_type,
    u.document_number,
    u.city,
    u.country
FROM users u 
WHERE birth_date > '2008-01-01';
```

## 2 Vista: Contacto de Usuarios
### 📌 Descripción
- Crea una vista con la información de contacto del usuario.

- Genera full_name

- Usa COALESCE para mostrar:

- mobile

- phone

- o 'Sin teléfono' si ambos son NULL

``` sql
CREATE VIEW briam_user_contacts AS
SELECT 
    CONCAT(first_name, ' ', last_name) AS full_name,
    email,
    COALESCE(mobile, phone, 'Sin teléfono') AS contact_number,
    address,
    city,
    state,
    country
FROM users;
```

## 3 Vista: Usuarios con Ingresos
### 📌 Descripción
- Muestra únicamente usuarios que tengan ingresos mayores a 0.
``` sql
CREATE VIEW briam_users_with_income AS
SELECT 
    u.id,
    u.first_name,
    u.last_name,
    u.profession,
    u.monthly_income
FROM users u 
WHERE monthly_income > 0;
```
### 📊 Consulta: Cantidad de usuarios por ingreso
``` sql
SELECT 
    monthly_income, 
    COUNT(*) AS total_users
FROM users
GROUP BY monthly_income
ORDER BY monthly_income DESC;
```

# 4 Vista: Resumen Demográfico
### 📌 Descripción

- Nombre completo (full_name)

- Edad calculada

- Género

- Estado civil

- Nivel educativo

- Ciudad

- País
``` sql
CREATE VIEW briam_view_demographic_summary AS
SELECT 
    CONCAT(first_name, ' ', last_name) AS full_name,
    TIMESTAMPDIFF(YEAR, birth_date, CURDATE()) AS age,
    gender,
    marital_status,
    education_level,
    city,
    country
FROM users;
```
### 📊 Consulta: Usuarios por Ciudad
``` sql
SELECT 
    city, 
    COUNT(*) AS total_users
FROM briam_view_demographic_summary
GROUP BY city
ORDER BY total_users DESC;
```
## 5 Vista: Perfil Completo de Usuario
### 📌 Descripción

- Identificación

- Edad

- Información profesional

- Ingresos

- Ubicación
``` sql
CREATE VIEW briam_view_user_profile AS
SELECT 
    CONCAT(first_name, ' ', last_name) AS full_name,
    document_type,
    document_number,
    TIMESTAMPDIFF(YEAR, birth_date, CURDATE()) AS age,
    profession,
    education_level,
    company,
    monthly_income,
    city,
    country
FROM users;
```
### 📊 Consulta: Usuarios con ingresos mayores a 3,000,000
``` sql
SELECT * 
FROM briam_view_user_profile
WHERE monthly_income > 3000000
ORDER BY city ASC;
``` 
## Resumen General
## En este documento se crearon:
- 5 Vistas (VIEW)

- 3 Consultas de análisis

- Uso de:

- CONCAT

- COALESCE

- TIMESTAMPDIFF

- GROUP BY

- ORDER BY

- WHERE