# Property API

REST API construida con NestJS para gestión de propiedades.

## Descripción

API RESTful que incluye autenticación JWT, gestión de usuarios y productos, con soporte para MongoDB.

## Características

- 🔐 Autenticación JWT
- 👤 Gestión de usuarios
- � CRUD de productos/propiedades
- �🗃️ Base de datos MongoDB con Mongoose
- 🌱 Sistema de seed para datos iniciales
- ✅ Validación de datos con class-validator
- 🧪 Testing configurado

## Tecnologías

- **Framework**: NestJS
- **Base de datos**: MongoDB
- **Autenticación**: JWT + Passport
- **Validación**: class-validator, class-transformer
- **Testing**: Jest

## Instalación

```bash
npm install
```

## Configuración

Crear archivo `.env` con las siguientes variables:

```env
DATABASE_URL=mongodb://localhost:27017/mi_base_de_datos
JWT_SECRET=mi_clave_secreta_jwt
```

## Arquitectura

```
src/
├── auth/              # Módulo de autenticación
│   ├── dto/          # DTOs para auth
│   ├── guards/       # Guards JWT y Local
│   └── strategies/   # Estrategias de Passport
├── users/            # Módulo de usuarios
│   ├── dto/          # DTOs de usuarios
│   └── schemas/      # Esquemas MongoDB
├── products/         # Módulo de productos/propiedades  
│   ├── dto/          # DTOs de productos
│   └── schemas/      # Esquemas MongoDB
└── seed/             # Módulo para poblar BD
```

**Patrón de arquitectura**: Modular con separación de responsabilidades
- **Controllers**: Manejan las peticiones HTTP
- **Services**: Lógica de negocio
- **DTOs**: Validación y transformación de datos
- **Guards**: Protección de rutas
- **Schemas**: Modelos de base de datos

## Ejecución

```bash
# Desarrollo
npm run start:dev

# Producción
npm run start:prod
```

## Endpoints principales

### Autenticación
- `POST /auth/login` - Login de usuario

### Usuarios  
- `GET /users` - Listar usuarios

### Productos/Propiedades    *(Próximamente)*
- `GET /products` - Listar productos
- `GET /products/:id` - Obtener producto por ID
- `POST /products` - Crear producto 

### Utilidades
- `POST /seed` - Poblar base de datos

## Testing

```bash
# Tests unitarios
npm run test

# Tests e2e
npm run test:e2e
```

## Despliegue en Render

### Configuración automática
Este proyecto incluye un archivo `render.yaml` para despliegue automático en Render.

### Variables de entorno en Render
Configurar las siguientes variables en el dashboard de Render:

```
MONGODB_URI=tu_conexion_mongodb_atlas
JWT_SECRET=tu_clave_jwt_secreta
JWT_EXPIRES_IN=1d
NODE_ENV=production
CORS_ORIGIN=https://tu-frontend.vercel.app
```

### Comandos de build
- **Build Command**: `npm run render:build`
- **Start Command**: `npm run start:prod`
