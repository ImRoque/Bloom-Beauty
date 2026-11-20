# Bloom Beauty

**Bloom Beauty** es una tienda en línea enfocada en productos de cuidado de la piel (*skincare*), cuidado capilar y accesorios ecológicos. El proyecto fue diseñado en Figma y desarrollado como una aplicación web con catálogo interactivo, carrito de compras, integración de pagos con PayPal y gestión de usuarios con PHP y MySQL.

## Objetivo

Ofrecer una plataforma de comercio electrónico con una interfaz limpia donde los usuarios puedan consultar productos de cosmética natural (ingredientes, tipo de piel recomendado y si son veganos), filtrar el catálogo en tiempo real, gestionar su carrito de compras y completar el flujo de pago en línea.

## Arquitectura

- **Frontend:** Aplicación multipágina compuesta por las vistas de inicio (`index.html`), catálogo (`productos.html`), carrito (`carrito.html`), autenticación (`Login.html`, `registro.html`), perfil de usuario (`perfil.html`) y políticas (`politica.html`). La lógica en JavaScript (`productos.js`, `carrito.js`, `script.js`) renderiza el catálogo en el cliente y mantiene el estado del carrito en `localStorage`.
- **Backend:** Scripts en PHP (`login.php`, `registro.php`, `session.php`, `logout.php`, `cambiar_contrasena.php` y endpoints en `bd/bloombeauty/bloombeauty/`) que reciben peticiones asíncronas en formato JSON para autenticar usuarios, gestionar sesiones y actualizar credenciales.
- **Base de datos:** Base de datos relacional en MySQL (esquema base en `bd/db.txt`) con la tabla `usuarios` para almacenar y validar las cuentas registradas.


## Cómo ejecutar el proyecto localmente

1. **Requisitos:** Contar con un entorno local de Apache, PHP y MySQL (como **XAMPP**, **WAMP** o **Laragon**).
2. **Clonar el repositorio** dentro de la carpeta pública de tu servidor web (por ejemplo, `htdocs` en XAMPP) conservando el nombre de carpeta `Bloom-Beauty`:
   ```bash
   git clone https://github.com/ImRoque/Bloom-Beauty.git
   ```
3. **Configurar la base de datos:** Inicia MySQL y ejecuta en phpMyAdmin o en tu cliente SQL el esquema de la tabla `usuarios` (basado en `bd/db.txt`) sobre la base de datos `bloom` que utiliza `conexion.php`:
   ```sql
   CREATE DATABASE IF NOT EXISTS bloom;
   USE bloom;

   CREATE TABLE usuarios (
       id INT PRIMARY KEY AUTO_INCREMENT,
       nombre VARCHAR(50) NOT NULL,
       correo VARCHAR(100) NOT NULL UNIQUE,
       contrasena VARCHAR(255) NOT NULL
   );
   ```
4. **Verificar credenciales locales:** Revisa que los parámetros en `conexion.php` coincidan con tu entorno MySQL (por defecto: servidor `localhost`, usuario `root` y contraseña vacía `""`).
5. **Abrir la aplicación:** Inicia Apache y entra desde el navegador a:
   ```text
   http://localhost/Bloom-Beauty/index.html
   ```
