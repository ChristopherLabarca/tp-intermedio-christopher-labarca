# Backend Stock MongoDB 📦

Sistema de gestión de stock de productos con autenticación JWT, construido con Node.js, Express, TypeScript y MongoDB.

## 🎯 Características

- ✅ Autenticación con JWT (registro y login)
- ✅ Roles de usuario (admin, user)
- ✅ CRUD completo para productos y categorías
- ✅ Rutas protegidas con autenticación
- ✅ Validación de datos con express-validator
- ✅ Base de datos MongoDB con Mongoose
- ✅ TypeScript para tipado estático
- ✅ Estructura MVC clara y escalable

## 📋 Requisitos Previos

- **Node.js** v18+ ([descargar](https://nodejs.org/))
- **MongoDB** corriendo localmente o acceso a MongoDB Atlas
- **npm** o **yarn**

## 🚀 Instalación

1. **Clonar o descargar el proyecto:**
```bash
cd backend-stock-mongo
```

2. **Instalar dependencias:**
```bash
npm install
```

3. **Configurar variables de entorno:**

Crear o editar el archivo `.env` en la raíz del proyecto:

```env
# Puerto del servidor
PORT=3000

# Conexión a MongoDB
MONGODB_URI=mongodb://localhost:27017/stock_db
# O para MongoDB Atlas:
# MONGODB_URI=mongodb+srv://usuario:contraseña@cluster.mongodb.net/stock_db

# Configuración JWT
JWT_SECRET=tu_secreto_super_seguro_minimo_32_caracteres
JWT_EXPIRES_IN=1d
```

⚠️ **Importante:** El `JWT_SECRET` debe ser una cadena segura y larga.

## ▶️ Ejecutar el Proyecto

### Modo Desarrollo
```bash
npm run dev
```

El servidor estará disponible en `http://localhost:3000`

### Modo Producción
```bash
npm run build
npm start
```

## 📚 Estructura del Proyecto

```
src/
├── controllers/          # Controladores (HTTP handlers)
├── services/             # Lógica de negocio
├── models/               # Esquemas y modelos Mongoose
├── routes/               # Definición de rutas
├── middlewares/          # Middlewares personalizados
├── validators/           # Validadores de datos
├── types/                # Definiciones TypeScript
├── config/               # Configuración (BD, etc)
└── index.ts              # Punto de entrada
```

## 🔐 Autenticación

### Registro de Usuario
```bash
POST /auth/register
Content-Type: application/json

{
  "username": "juan123",
  "email": "juan@example.com",
  "password": "miPassword123"
}
```

**Respuesta exitosa (201):**
```json
{
  "message": "Usuario creado exitosamente"
}
```

### Login de Usuario
```bash
POST /auth/login
Content-Type: application/json

{
  "email": "juan@example.com",
  "password": "miPassword123"
}
```

**Respuesta exitosa (200):**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

## 📦 Endpoints

### Rutas Públicas

#### Saludo
```bash
GET /api/saludo
```

#### Acceso Público
```bash
GET /public
```

### Rutas Protegidas

Todas las rutas protegidas requieren un token JWT en el header:
```bash
Authorization: Bearer <token>
```

#### Categorías

| Método | Ruta | Descripción | Rol |
|--------|------|-------------|-----|
| `GET` | `/api/categoria` | Listar todas las categorías | Público |
| `GET` | `/api/categoria/:id` | Obtener categoría por ID | Público |
| `POST` | `/api/categoria` | Crear nueva categoría | Admin |
| `PUT` | `/api/categoria/:id` | Actualizar categoría | Admin |
| `DELETE` | `/api/categoria/:id` | Eliminar categoría | Admin |

**Ejemplo - Crear categoría:**
```bash
POST /api/categoria
Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "Electrónica",
  "description": "Productos electrónicos"
}
```

#### Productos

| Método | Ruta | Descripción | Rol |
|--------|------|-------------|-----|
| `GET` | `/api/producto` | Listar todos los productos | Público |
| `GET` | `/api/producto/:id` | Obtener producto por ID | Público |
| `POST` | `/api/producto` | Crear nuevo producto | Admin |
| `PUT` | `/api/producto/:id` | Actualizar producto | Admin |
| `DELETE` | `/api/producto/:id` | Eliminar producto | Admin |

**Ejemplo - Crear producto:**
```bash
POST /api/producto
Authorization: Bearer <token>
Content-Type: application/json

{
  "name": "Laptop",
  "description": "Laptop de última generación",
  "price": 999.99,
  "stock": 5,
  "categoryId": "67b1a2c3d4e5f6g7h8i9j0k1"
}
```

## 🔑 Sistema de Roles

- **user**: Usuario normal (rol por defecto)
- **admin**: Administrador (puede crear, actualizar, eliminar)

## 🛠️ Scripts Disponibles

```bash
# Desarrollo con hot reload
npm run dev

# Build para producción
npm run build

# Iniciar en modo producción
npm start

# Ejecutar linter (si está configurado)
npm run lint
```

## 📄 Archivos de Configuración

- `tsconfig.json` - Configuración de TypeScript
- `.env` - Variables de entorno (no incluir en git)
- `package.json` - Dependencias y scripts

## 🐛 Solución de Problemas

### Error: `MongoDB connection failed`
- Verificar que MongoDB está corriendo
- Verificar `MONGODB_URI` en `.env`
- Para Atlas: verificar credenciales y whitelist de IP

### Error: `JWT_SECRET no definido`
- Asegurarse de completar `JWT_SECRET` en `.env`

### Error: `Cannot find module 'mongoose'`
- Ejecutar `npm install`
- Verificar que `node_modules` existe

## 🧪 Prueba de Endpoints

Se incluye archivo `Insomnia_2026-01-27.yaml` con todas las rutas configuradas para testear fácilmente.

También existe `curls.md` con ejemplos de curl para las peticiones HTTP.

## 📦 Dependencias Principales

- **express** - Framework web
- **mongoose** - ODM para MongoDB
- **jsonwebtoken** - Autenticación JWT
- **bcrypt** - Encriptación de contraseñas
- **express-validator** - Validación de datos
- **typescript** - Lenguaje tipado
- **dotenv** - Manejo de variables de entorno

## 📝 Licencia

ISC

## 👤 Autor

Curso UTN 999198248

---

**Última actualización:** 28 de enero de 2026
