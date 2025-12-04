# API de Productos – Talento Tech

API REST construida con Node.js y Express para gestionar productos, incluyendo autenticación con JWT y operaciones CRUD protegidas.

## Tecnologías

- Node.js  
- Express  
- JWT (JSON Web Tokens)  
- CORS  
- Postman (para pruebas)

## Requisitos previos

- Node.js instalado  
- npm o yarn  
- Archivo `.env` con al menos:

```env
PORT=3000
JWT_SECRET_KEY=tu_clave_secreta
```

## Instalación

```bash
# Clonar el repositorio
git clone https://github.com/tu-usuario/tu-repo.git
cd tu-repo

# Instalar dependencias
npm install

# Iniciar el servidor
npm start
```

El servidor se levanta por defecto en `http://localhost:3000`.

## Endpoints principales

### Autenticación

#### POST `/api/login`

Devuelve un token JWT de prueba.

Body de ejemplo:

```json
{
  "email": "test@gmail.com",
  "password": "123456"
}
```

Respuesta de ejemplo:

```json
{
  "token": "JWT_TOKEN_AQUI"
}
```

### Productos

> Los endpoints protegidos requieren header `Authorization: Bearer <token>`.

#### GET `/api/products`

Obtiene todos los productos.

#### GET `/api/products/:id`

Obtiene un producto por su ID.

#### POST `/api/products/create`

Crea un nuevo producto.

Headers:

```text
Authorization: Bearer JWT_TOKEN_AQUI
Content-Type: application/json
```

Body de ejemplo:

```json
{
  "nombre": "Producto de prueba",
  "precio": 1000,
  "descripcion": "Descripción de ejemplo"
}
```

#### DELETE `/api/products/:id`

Elimina un producto existente.

Respuesta típica:

```json
{
  "message": "Producto eliminado"
}
```

## Middleware de autenticación

La autenticación se realiza mediante un middleware que:

- Lee el header `Authorization`  
- Verifica el token JWT  
- Devuelve `401` si no hay token y `403` si es inválido  

Esto permite proteger rutas como creación y eliminación de productos.

## Notas

- El proyecto está pensado como práctica de backend para Talento Tech.  