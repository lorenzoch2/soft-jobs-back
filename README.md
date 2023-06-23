# Soft Jobs Back

Este es el backend para la aplicación Soft Jobs.

## Configuración de la base de datos

1. Ejecuta el script `softjobs.sql` en tu servidor de base de datos para crear la base de datos `softjobs` y la tabla `usuarios`.

```sql
CREATE DATABASE softjobs;
\c softjobs;
CREATE TABLE usuarios (
  id SERIAL,
  email VARCHAR(50) NOT NULL,
  password VARCHAR(60) NOT NULL,
  rol VARCHAR(25),
  lenguage VARCHAR(20)
);
SELECT * FROM usuarios;
```

2. Configura las variables de entorno en un archivo `.env` con las siguientes variables:

```
DB_HOST=<tu_host_de_base_de_datos>
DB_USER=<tu_usuario_de_base_de_datos>
DB_PASSWORD=<tu_contraseña_de_base_de_datos>
DB_DATABASE=softjobs
SECRET_KEY=<tu_clave_secreta_para_JWT>
```

## Instalación

1. Clona este repositorio en tu máquina local.

2. Ejecuta `npm install` para instalar las dependencias.

3. Ejecuta `npm run dev` para iniciar el servidor en modo de desarrollo.

## Endpoints

- `POST /usuarios`: Registra un nuevo usuario en la base de datos. Debe incluir los siguientes campos en el cuerpo de la solicitud: `email`, `password`, `rol` y `lenguage`.

- `POST /login`: Inicia sesión con las credenciales de un usuario registrado. Debe incluir los campos `email` y `password` en el cuerpo de la solicitud. Retorna un token JWT válido en caso de éxito.

- `GET /usuarios`: Obtiene los detalles del usuario autenticado. Debe incluir el token JWT en la cabecera de la solicitud con la siguiente estructura: `Authorization: Bearer <token>`. Retorna los detalles del usuario sin incluir la contraseña.

## Dependencias

- bcryptjs: ^2.4.3
- cors: ^2.8.5
- dotenv: ^16.3.1
- express: ^4.18.2
- jsonwebtoken: ^9.0.0
- nodemon: ^2.0.22
- pg: ^8.11.0
- pg-format: ^1.0.4
