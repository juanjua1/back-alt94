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

### Configuración en Render Dashboard
1. **Conectar tu repositorio** de GitHub
2. **Build Command**: `npm install && npm run build`
3. **Start Command**: `npm run start:prod`
4. **Node Version**: 18.18.0 (especificado en .nvmrc)

### Variables de entorno requeridas
Configurar en el dashboard de Render:

```
MONGODB_URI=mongodb+srv://usuario:password@cluster.mongodb.net/database
JWT_SECRET=tu_clave_jwt_secreta_muy_larga
JWT_EXPIRES_IN=1d
NODE_ENV=production
CORS_ORIGIN=https://alt94-front.vercel.app
NODE_OPTIONS=--max-old-space-size=1024
```

### Solución de problemas comunes
- **Error de memoria**: Variable `NODE_OPTIONS=--max-old-space-size=1024` ya incluida
- **Puerto no detectado**: El código usa `process.env.PORT` automáticamente
- **Seed en producción**: Deshabilitado automáticamente en NODE_ENV=production
