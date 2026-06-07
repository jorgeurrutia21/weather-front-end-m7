# Weather-Front-End-m7

## Descripción

Aplicación web desarrollada con Vue 3 que permite consultar información meteorológica de distintas ciudades utilizando la API Open-Meteo.

En esta versión se incorporó un sistema de autenticación de usuarios mediante Firebase Authentication y almacenamiento de datos en Firestore, permitiendo personalizar la experiencia según el usuario conectado.

---

## Funcionalidades principales

- Consulta de información climática.
- Registro de usuarios.
- Inicio de sesión.
- Cierre de sesión.
- Gestión de lugares favoritos.
- Preferencias de temperatura (Celsius o Fahrenheit).
- Persistencia de datos mediante Firebase Firestore.
- Rutas protegidas para usuarios autenticados.

---

## Sistema de usuarios

Cada usuario registrado almacena la siguiente información:

- UID generado por Firebase(identificador unico de usuario).
- Nombre.
- Correo electrónico.
- Lista de lugares favoritos.
- Preferencia de temperatura (°C o °F).
- Fecha de registro.

La información del usuario se gestiona mediante Pinia como estado global de la aplicación.

---

## Rutas de la aplicación

-Ruta Descripción

-/ Página = principal
-/lugar/ = :id Detalle de una ubicación
-/about = Información del proyecto
-/login = Inicio de sesión
-/registro = Registro de usuarios
-/favoritos = Lugares favoritos (ruta protegida)

---

## Protección de rutas

La ruta /favoritos requiere que el usuario haya iniciado sesión.

Si un usuario intenta acceder sin estar autenticado, el sistema lo redirige automáticamente a una ruta pública.

---

## Personalización por usuario

La aplicación adapta parte de la interfaz según el usuario autenticado:

- Muestra el correo del usuario en el Navbar.
- Permite guardar y eliminar lugares favoritos.
- Permite seleccionar la unidad de temperatura:
- Celsius (°C)
- Fahrenheit (°F)

Estas preferencias se almacenan en Firestore y son recuperadas al iniciar sesión.

---

## Tecnologías utilizadas

- Vue 3
- Vue Router
- Pinia
- Firebase Authentication
- Firebase Firestore
- Bootstrap 5
- Open-Meteo API

---

## Instalación y ejecución

Para ejecutar este proyecto de manera local:

1. Clonar o descargar el repositorio:  
   https://github.com/jorgeurrutia21/weather-front-end-m7

2. Boton derecho en la carpeta del proyecto y abrir la consola Git Bash Here.

3. Ejecutar los comandos pnpm install para instalar los node-modules y pnpm dev para ingresar al app.

4. Ingresar a esta URL http://localhost:5173 para ver la app.

## Objetivo del proyecto

El objetivo principal es entregar información meteorológica de distintas ciudades de Chile, permitiendo al usuario consultar tanto el clima actual como el pronóstico estimado para los próximos 7 días de diferentes ciudades de Chile.

---

## Autor

_Jorge Urrutia_
