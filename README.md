# BodegaTech — Script de Inventario

Script SQL para crear y poblar la tabla de inventario de BodegaTech, registrar movimientos de stock y ejecutar consultas básicas de validación.

## Requisitos

- PostgreSQL 12 o superior
- Cliente de SQL (pgAdmin4)

## Contenido del script

El archivo `inventario.sql` está organizado en pasos:

1. **Paso 1 — Eliminar tabla existente:** borra la tabla `inventario` si ya existe, para poder ejecutar el script desde cero sin conflictos.
2. **Paso 2 — Crear tabla:** define la estructura de `inventario` con sus columnas y tipos de datos.
3. **Paso 3 — Insertar productos:** carga 10 productos de ejemplo con su categoría, precio, stock y estado.
4. **Paso 4 — Actualizar ventas del día:** descuenta unidades vendidas del stock de algunos productos.
5. **Paso 5 — Descontinuar producto:** marca un producto como inactivo (`activo = FALSE`).
6. **Paso 6 — Consultas de validación:** incluye tres consultas de ejemplo:
   - Inventario completo ordenado por categoría.
   - Productos activos con stock igual o por debajo del mínimo.
   - Valor total del stock activo, agrupado por categoría.

## Estructura de la tabla `inventario`

| Columna          | Tipo          | Descripción                                              |
|------------------|---------------|-----------------------------------------------------------|
| id_producto      | INT           | Identificador único del producto (clave primaria)        |
| nombre_producto  | VARCHAR(100)  | Nombre del producto                                       |
| categoria        | VARCHAR(50)   | Categoría a la que pertenece el producto                  |
| precio_unitario  | DECIMAL(10,2) | Precio de venta en USD                                     |
| stock_actual     | INT           | Unidades disponibles actualmente                           |
| stock_minimo     | INT           | Unidades mínimas antes de requerir reposición              |
| fecha_ingreso    | DATE          | Fecha en que el producto ingresó al inventario              |
| activo           | BOOLEAN       | `TRUE` si está disponible, `FALSE` si fue descontinuado    |

## Cómo ejecutarlo

1. Conectate a tu base de datos de PostgreSQL.
2. Ejecutá el script completo:
   ```bash
   psql -U usuario -d nombre_base_de_datos -f inventario.sql
   ```
   O bien copiá y pegá el contenido en tu cliente SQL preferido (pgAdmin, DBeaver, etc.).
3. Revisá los resultados de las consultas del Paso 6 para validar que los datos se cargaron correctamente.

## Notas

- El script asume que la base de datos ya existe; solo crea y gestiona la tabla `inventario` dentro de ella.
- Si necesitás volver a correr el script completo, no hace falta modificar nada: el Paso 1 se encarga de eliminar la tabla anterior antes de recrearla.

## Autor

Valdez Rocio
