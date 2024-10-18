# API de Gestión de Usuarios  
Esta API permite gestionar usuarios mediante un CRUD (Crear, Leer, Actualizar, Eliminar) utilizando **FastAPI** como framework backend y **PostgreSQL** como base de datos. Incluye protección mediante **JWT** para asegurar los endpoints.  

## **Requisitos previos**  
1. Python 3.8 o superior.  
2. PostgreSQL instalado y en ejecución.  
3. Un entorno virtual para manejar dependencias (opcional pero recomendado).  

## **Instalación y configuración**  

### 1. Clonar el repositorio  
```bash
git clone <URL_DEL_REPOSITORIO>
cd <NOMBRE_DEL_REPOSITORIO>

2. Crear y activar un entorno virtual
bash
Copy code
python -m venv venv
source venv/bin/activate  # En Linux/macOS
# En Windows:
# venv\Scripts\activate
3. Instalar las dependencias
bash
Copy code
pip install -r requirements.txt
4. Configurar la base de datos PostgreSQL
Crea una base de datos llamada user_db en PostgreSQL.

sql
Copy code
CREATE DATABASE user_db;
Actualiza el archivo database.py con las credenciales correctas de PostgreSQL:

python
Copy code
DATABASE_URL = "postgresql://<usuario>:<contraseña>@localhost:5432/user_db"
5. Ejecutar las migraciones de la base de datos
bash
Copy code
python init_db.py  # Crea las tablas en la base de datos
Cómo ejecutar la API
Ejecuta el servidor de desarrollo con el siguiente comando:

bash
Copy code
uvicorn main:app --reload
Esto iniciará la API en http://localhost:8000.

Rutas de la API
Crear un usuario
POST /users/
Crea un nuevo usuario en la base de datos.

Body (JSON):

json
Copy code
{
  "email": "example@gmail.com",
  "name": "John Doe",
  "password": "password123"
}
Consultar un usuario
GET /users/{user_id}
Obtiene la información de un usuario específico por su ID.

Actualizar un usuario
PUT /users/{user_id}
Actualiza los datos de un usuario existente.

Body (JSON):

json
Copy code
{
  "name": "Jane Doe",
  "password": "newpassword456"
}
Eliminar un usuario
DELETE /users/{user_id}
Elimina un usuario de la base de datos.

Autenticación JWT
Cada endpoint está protegido con JWT. Al autenticarte, recibirás un token que deberás enviar en el header de las peticiones.

Header de autorización:

bash
Copy code
Authorization: Bearer <tu_token_jwt>
Pruebas Unitarias
Las pruebas se realizan con Pytest. Para ejecutarlas:

bash
Copy code
pytest
Estructura del proyecto
bash
Copy code
├── main.py           # Archivo principal de la aplicación
├── models.py         # Modelos ORM (SQLAlchemy)
├── schemas.py        # Esquemas de validación (Pydantic)
├── database.py       # Configuración de la base de datos
├── init_db.py        # Script para inicializar la base de datos
├── requirements.txt  # Dependencias del proyecto
└── tests/            # Directorio de pruebas
Dependencias
FastAPI
SQLAlchemy
PostgreSQL
PyJWT
Uvicorn
Pytest
Instálalas con:

bash
Copy code
pip install -r requirements.txt
Notas adicionales
Si deseas desplegar la API en producción, asegúrate de configurar variables de entorno para la conexión a la base de datos y el secreto JWT.
Implementar un sistema de paginación en GET /users/ es una mejora opcional recomendada si se espera manejar un alto volumen de datos.
Contacto