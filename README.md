Proyecto: LinkTic - Sistema de Gestión y Reserva de Servicios DEPLOY
Este proyecto es un sistema de reservas de servicios que incluye la funcionalidad de reserva, modificación, cancelación y visualización de reservas. El sistema está construido con una arquitectura fullstack que incluye un frontend desarrollado en React/Next.js y un backend en NestJS. Los datos se gestionan mediante PostgreSQL/MySQL y se implementan opciones de autenticación y despliegue en la nube.

Arquitectura
El proyecto utiliza una arquitectura monolítica modular con planes de escalabilidad a microservicios si se requiere mayor flexibilidad. La modularidad del proyecto permite dividir las funcionalidades en diferentes módulos del backend, como el módulo de usuarios, el módulo de reservas y el módulo de autenticación. El frontend sigue una arquitectura basada en componentes que permite un desarrollo y mantenimiento eficiente.

La decisión de utilizar esta arquitectura se tomó en función de la facilidad de desarrollo en un equipo pequeño y la capacidad de escalar el proyecto conforme crezca la base de usuarios.

Despliegue en la Nube
Este proyecto está configurado para ser desplegado en AWS utilizando EC2 y RDS para la base de datos. Además, se utilizaron servicios como S3 para almacenar archivos estáticos y CloudFront para la distribución de contenido.

Para simular el entorno local, se utilizó LocalStack, lo que permitió emular los servicios de AWS localmente, haciendo las pruebas de integración más sencillas.

Prácticas DevOps
Se implementó una pipeline CI/CD utilizando GitHub Actions. Esta pipeline incluye las siguientes fases:

Test automático: Se ejecutan pruebas unitarias y de integración cada vez que se realiza un push.
Versionado automático: El sistema utiliza semantic-release para versionar el código automáticamente basándose en los commits realizados.
Generación de changelog: Cada versión nueva genera un changelog automáticamente, lo cual facilita el rastreo de cambios.
Despliegue continuo: Al aprobar los cambios en la rama main, el sistema despliega automáticamente los servicios en la infraestructura de AWS.
Backend
El backend está desarrollado en NestJS y expone una serie de API RESTful para interactuar con los diferentes servicios del sistema, incluyendo:

Gestión de usuarios: Registro, inicio de sesión y autenticación basada en JWT.
Gestión de reservas: Endpoints para crear, modificar, cancelar y visualizar reservas.
Gestión de roles: Diferentes permisos según el rol del usuario (administrador, usuario regular).
El código sigue estrictamente las mejores prácticas de desarrollo como la inyección de dependencias, manejo adecuado de excepciones y pruebas unitarias para asegurar la calidad del código.

Frontend
El frontend del proyecto está desarrollado utilizando React y Next.js. El diseño de la interfaz sigue los principios de UI/UX modernos y permite una experiencia de usuario fluida e intuitiva. Algunas de las funcionalidades principales incluyen:

Formulario dinámico de reservas: Los usuarios pueden seleccionar el servicio, la fecha y hora disponibles y reservar de manera fácil e intuitiva.
Panel de control de reservas: Los usuarios pueden visualizar sus reservas activas, modificar o cancelarlas.
Autenticación: El frontend está completamente integrado con el backend para manejar la autenticación y autorización de usuarios.
Instrucciones de Instalación
Clonar el repositorio:

bash
Npm run
Instalar las dependencias del frontend y backend:

bash
Copy code
cd frontend
npm install
cd ../backend
npm install
Configurar las variables de entorno: Crear un archivo .env en el directorio raíz del backend con las siguientes variables:

bash
Copy code
DB_HOST=localhost
DB_PORT=5432
DB_USER=usuario
DB_PASSWORD=contraseña
JWT_SECRET=clave_secreta
Iniciar la base de datos local:

bash
Copy code
docker-compose up
Iniciar el backend:

bash
Copy code
npm run start:dev
Iniciar el frontend:

para el sql lea el admin!! IMPORTANTE
Bases de dato write app
mysql -u root -p  
SELECT user, host FROM mysql.user;
GRANT ALL PRIVILEGES ON _._ TO 'admin'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
SHOW GRANTS FOR 'admin'@'localhost';

bash
Copy code
npm run dev
Funcionalidades Avanzadas (Bonus)
Autenticación y Autorización: Implementación de JWT para garantizar que solo usuarios autenticados puedan acceder a los recursos protegidos.
Actualizaciones en tiempo real: Utilización de WebSockets para notificaciones en tiempo real sobre cambios en las reservas.
Documentación de API: Integración con Swagger para documentar y probar los endpoints de la API.
Despliegue: El proyecto está desplegado en AWS y accesible online.
