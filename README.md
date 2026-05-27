# Proyecto Integrador: Base de Datos Empresarial

## Descripción
Este proyecto simula una base de datos real para una empresa ficticia, organizada en tres esquemas que representan diferentes áreas de negocio: Ventas, Logística y Marketing. El objetivo es demostrar el diseño relacional, la integridad referencial y la organización profesional de datos.

---

## Estructura de la Base de Datos

### 1. Schema VENTAS
Gestiona toda la información relacionada con clientes y productos.

#### Tabla: CLIENTE
- **dni** (INT) - Identificador único del cliente. Se eligió como PK porque es un dato natural y único en Argentina.
- **nombre** (VARCHAR 50) - Nombre del cliente
- **apellido** (VARCHAR 100) - Apellido del cliente
- **fecha_registro** (DATE) - Fecha en que el cliente se registró en el sistema

**Decisión de diseño:** El DNI como PK es más eficiente que un ID artificial porque ya es único en la realidad.

#### Tabla: PRODUCTOS
- **id_producto** (INT) - Identificador único del producto. AUTO_INCREMENT no se usó para permitir IDs personalizados.
- **nombre_producto** (VARCHAR 100) NOT NULL - Nombre obligatorio del producto
- **fecha_elaboracion** (DATE) - Cuándo se fabricó el producto
- **fecha_vencimiento** (DATE) NOT NULL - Fecha de vencimiento obligatoria por razones de seguridad alimentaria

**Decisión de diseño:** Se marcó como NOT NULL la fecha de vencimiento porque es crítica para productos con fecha de caducidad.

---

### 2. Schema LOGISTICA
Gestiona la información de transportistas y envíos.

#### Tabla: TRANSPORTISTAS
- **dni_chofer** (INT) - Identificador único del transportista. Se eligió DNI como PK porque es el dato más natural.
- **nombre** (VARCHAR 50) - Nombre del transportista
- **apellido** (VARCHAR 70) - Apellido del transportista
- **sueldo** (DECIMAL) - Sueldo del transportista. Se usó DECIMAL en lugar de INT para permitir decimales en moneda.

**Decisión de diseño:** Se utilizó DECIMAL para sueldo porque el dinero requiere precisión decimal, no números enteros.

---

### 3. Schema MARKETING
Gestiona campañas publicitarias y promociones.

#### Tabla: CAMPANAS
- **id_campana** (INT) - Identificador único de la campaña
- **nombre_campana** (VARCHAR 100) NOT NULL - Nombre obligatorio de la campaña
- **descripcion** (TEXT) - Descripción detallada de la campaña sin límite de caracteres
- **presupuesto** (DECIMAL) - Presupuesto asignado a la campaña

**Decisión de diseño:** Se usó TEXT para descripción porque permite textos largos sin límite fijo. Se marcó nombre_campana como NOT NULL porque toda campaña debe tener un nombre.

---

## Decisiones Generales de Diseño

1. **Tipos de Datos:**
   - INT para identificadores y números enteros
   - VARCHAR(n) para textos con límite (nombres, apellidos)
   - TEXT para descripciones largas sin límite fijo
   - DATE para fechas
   - DECIMAL para valores monetarios

2. **Claves Primarias:**
   - Se utilizaron datos naturales (DNI) cuando era posible
   - Se usó INT para IDs artificiales en productos y campañas

3. **Restricciones:**
   - Se aplicó NOT NULL solo a columnas críticas (nombres, fechas de vencimiento)

4. **Organización por Schemas:**
   - VENTAS: información comercial (clientes y productos)
   - LOGISTICA: información de transporte
   - MARKETING: información publicitaria
   - Esta separación permite que cada departamento trabaje de forma independiente

---

## Cómo Ejecutar el Script

1. Abre tu cliente SQL (MySQL Workbench, SQL Server Management Studio, DBeaver, etc.)
2. Copia todo el contenido del archivo `modulo2_coderhouse`
3. Pégalo en tu cliente SQL
4. Ejecuta el script completo
5. Verifica que se crearon los 3 esquemas y sus respectivas tablas

---

## Consideraciones Futuras

- Agregar claves foráneas (FK) para conectar tablas de distintos esquemas
- Crear índices en columnas frecuentemente consultadas
- Definir usuarios y permisos por departamento
- Crear vistas para reportes comunes

---

**Autor:** Ignacio Garcia Lombardini
**Fecha:** Mayo 2026  
**Estado:** Proyecto Integrador completado
