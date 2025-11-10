# Módulo Contenedores y Virtualización.

 ## 🐾 AdoptAPI — Descripción de los archivos del proyecto
A continuación se detallan los archivos principales que componen la aplicación AdoptAPI, una API REST desarrollada con FastAPI y SQLite, y desplegada mediante Docker.
### 🧠 main.py
Archivo principal de la aplicación FastAPI.
Define la instancia de la API, configura el sistema de logging y contiene los distintos endpoints REST:
/pets: gestión de mascotas (consulta y registro).
/persons: gestión de personas (consulta y registro).
/adoptions: registro de solicitudes de adopción.
/adoptions/{pet_id} (DELETE): permite revocar o eliminar una adopción existente.
Además, inicializa la base de datos y crea las tablas al arrancar la aplicación.
### 🧩 crud.py
Contiene las funciones encargadas de realizar las operaciones CRUD (Create, Read, Update, Delete) sobre la base de datos.
Actúa como capa intermedia entre la API (main.py) y el motor de base de datos (database.py).
### 🧱 models.py
Define las clases de modelo de SQLAlchemy, que representan las tablas de la base de datos:
Pet — información de las mascotas.
Person — información de las personas.
AdoptionRequest — solicitudes de adopción realizadas.
### 📦 schemas.py
Define los esquemas de validación Pydantic utilizados por FastAPI para asegurar que los datos de entrada y salida cumplan con la estructura esperada.
### 🗃️ database.py
Configura la conexión con la base de datos SQLite mediante SQLAlchemy.
Crea el motor (engine), la sesión (SessionLocal) y la base (Base), y permite que la aplicación utilice una base local o una ruta definida por variable de entorno (DATABASE_URL).
### ⚙️ requirements.txt
Lista de dependencias necesarias para ejecutar la aplicación, incluyendo:
FastAPI
Uvicorn
SQLAlchemy
Pydantic
Este archivo es utilizado durante la construcción de la imagen Docker para instalar las librerías requeridas.
### 🐋 Dockerfile
Define los pasos para construir la imagen Docker de la aplicación:
- Usa una imagen base ligera de Python 3.11.
- Copia los archivos del proyecto al contenedor.
- Instala las dependencias desde requirements.txt.
- Expone el puerto 8080.
- Ejecuta la aplicación FastAPI mediante Uvicorn.
### 🧩 docker-compose.yml
Archivo que orquesta la ejecución de la aplicación en un contenedor Docker.
- Construye la imagen definida en el Dockerfile.
- Expone el puerto 8080 al sistema huésped.
- Crea un volumen para persistir la base de datos SQLite.
