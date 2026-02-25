# Consultas en MongoDB

## Nivel 1 – Consultas Básicas

- Nivel 1 – Consultas Básicas

### 1 Listar todos los documentos de la colección users.
```JS
    db.users.find({},{_id:0, document_number:1})
```
### 2 Mostrar únicamente los campos first_name, last_name y email.
```JS
    db.users.find({},{first_name:1,last_name:1, email:1 })
```

### 3 Obtener todos los usuarios cuyo role sea "admin".
```JS
    db.users.find({role:"admind"},{})
```

### 4 Buscar los usuarios cuyo country sea "Colombia".
```JS
    db.users.find({country:"Colombia"},{})
```

### Listar los usuarios que estén activos (is_active = true).
```JS
    db.users.find({is_active:1},{})
```

### 6 Buscar los usuarios que no estén verificados (is_verified = false).
```JS
    db.users.find({is_verified:0},{})
```

### 7 Obtener los usuarios cuyo gender sea "Masculino".
```JS
    db.users.find({gender:"Masculino"},{})
```

### 8 Listar los usuarios que vivan en la ciudad "Medellín".
```JS
    db.users.find({gender:"Masculino"},{})
```

### 9 Buscar los usuarios que tengan al menos un hijo (children_count > 0).
```JS
    db.users.find({children_count:{$gt:0}},{})
```

### 10 Listar los usuarios cuya profesión (profession) no sea null.
```JS
    db.users.find({profession:{$ne:null}},{})
```

## Nivel 2 – Filtros con Operadores


### 11 Buscar usuarios con monthly_income mayor a 3000000.
```JS
    db.users.find({monthly_income: {$gte:3000000}},{})
```

### 12 Buscar usuarios con ingresos entre 2000000 y 5000000.
```JS
    db.users.find({
    monthly_income: {
        $gte: 2000000,
        $lte: 5000000
  }
})
```
### 13 Buscar usuarios cuya fecha de nacimiento sea posterior al 2000-01-01.
```JS
    db.usuarios.find({
    fechaNacimiento: {
        $gt: new Date("2000-01-01")
    }
    })
```

### 14 Buscar usuarios cuyo document_type esté en ["CC", "CE"].
```JS
    db.usuarios.find({
    document_type: {
        $in: ["CC", "CE"]
    }
    })
```

### 15 Buscar usuarios cuyo city no sea "Bogotá".
```JS
    db.usuarios.find({
    city: {
        $ne: "Bogotá"
    }
    })
```

### 16 Buscar usuarios cuyo nombre empiece por la letra "A".
```JS
    db.users.find({first_name: /^A/})
```

### 17 Buscar usuarios cuyo email termine en "gmail.com".
```JS
    db.users.find({email: /example.com$/})
```

### 18 Buscar usuarios que tengan más de 2 hijos y estén activos.
```JS
    db.users.find({children_count:{$gte: 2},
                is_active: 1
                }
                )
```

### 19 Buscar usuarios cuyo marital_status sea "Casado" y tengan hijos.
```JS
    db.users.find({marital_status:"Casado",children_count:{$gt:0}})
```

### 20 Buscar usuarios que estén inactivos o no verificados.
```JS

```
