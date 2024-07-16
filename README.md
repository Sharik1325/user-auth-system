# user-auth-system
Este proyecto es una solución completa para la gestión de usuarios, que incluye funcionalidades como creación de usuarios, inicio de sesión, cambio de contraseña y autenticación mediante OAuth con Google. Está diseñado para ser una referencia en la implementación de sistemas de autenticación seguros y eficientes.

**Funcionalidades principales**
Registro de usuarios
Inicio de sesión
Cambio y recuperación de contraseña
Autenticación mediante OAuth (Google)
Gestión de sesiones

**Tecnologías utilizadas**
Backend: Django, Django Rest Framework
Base de datos: SQLite (configuración por defecto, puede cambiarse a otra base de datos)
Autenticación: OAuth 2.0 (Google), JWT (JSON Web Tokens)

**Prerrequisitos**

Para clonar y ejecutar este proyecto en tu máquina local, necesitarás tener instalados los siguientes programas:

Python 3.10
pip (gestor de paquetes de Python)
virtualenv (opcional, pero recomendado)

**Instalación**
Pasos para configurar el proyecto en entorno local luego de clonar el repositorio:

1. Crear un entorno virtual (opcional, pero recomendado):
   python -m venv env 
   source env/bin/activate (Linux)  # En Windows usa `env\Scripts\activate`
2. Instalar las dependencias:
   pip install -r requirements.txt
3. Realiza las migraciones de la base de datos:
   python manage.py migrate
4. Crea un superusuario para acceder al admin de Django:
   python manage.py createsuperuser
5. Inicia el servidor de desarrollo:
   python manage.py runserver

**Uso**
Registro de usuarios:
Endpoint: POST /api/register/
  -Solicitud en formato JSON:
  {
    "email": "user@example.com",
    "password": "Password123!",
    "username": "exampleuser"
  }


Inicio de sesión:
Endpoint: POST /api/login/
  -Solicitud  en formato JSON:
  {
    "email": "user@example.com",
    "password": "Password123!"
}


Logout:
Endpoint: POST /api/logout-rest/
  -Solicitud  en formato JSON:
  {
    "refresh": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9..."
}


Cambio de contraseña:
Endpoint: POST /api/chage-password/
Autenticación requerida: JWT
  -Solicitud  en formato JSON:

{
    "old_password": "OldPassword123!",
    "new_password": "NewPassword123!",
    "confirm_new_password": "NewPassword123!"
}


 Recuperación de contraseña:
 Endpoint: POST /api/reset-password/
   -Solicitud  en formato JSON:
   {
    "email": "user@example.com"
}


Confirmación de recuperación de contraseña:
Endpoint: POST /api/reset-password/confirm/<uidb64>/<token>/
  -Solicitud  en formato JSON:
   {
    "new_password": "NewPassword123!",
    "confirm_new_password": "NewPassword123!"
}


Obtener información del usuario autenticado: 
Endpoint: GET /api/auth-user/
Autenticación requerida: JWT
  -Solicitud  en formato JSON:
  {
    "id": 1,
    "email": "user@example.com",
    "username": "exampleuser"
}

**Diccionario de respuestas:**

**Code 	Meaning**
USR001	User already exist 
USR002	User does not exist
USR003	Incorrect password
USR004	Successfully logged out
USR005	Exceeds number of attempts
USR006	Old wrong password
USR007	Password updated correctly
USR008	Passwords do not match
USR009	The account is already active
USR010	Invalid Token
USR011	The password has been reset successfully
USR012	Does not meet password requirements


   
