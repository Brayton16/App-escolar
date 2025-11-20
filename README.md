# **App-Escolar**

Plataforma integral de gestión académica compuesta por una aplicación web, una aplicación móvil y un backend unificado. El sistema está diseñado para instituciones educativas que requieren administrar estudiantes, profesores, encargados, cursos, secciones, grupos académicos, asignaciones, anuncios, entregas y comunicación interna.

Su arquitectura separa claramente las responsabilidades: la aplicación web sirve como panel administrativo, la aplicación móvil como herramienta para estudiantes y profesores, y el backend como núcleo de datos y lógica de negocio.

---

## **Descripción General de la Arquitectura**

El proyecto se divide en tres módulos principales:

La **aplicación web**, construida con Next.js, está orientada a administradores y personal académico. Permite gestionar cursos, profesores, estudiantes, secciones, grupos, anuncios y otros recursos institucionales desde una interfaz modular y extensible. La navegación está organizada en rutas separadas por rol y las páginas utilizan componentes reutilizables para mantener consistencia visual y de comportamiento.

La **aplicación móvil**, desarrollada con React Native y Expo, está enfocada en la experiencia directa del usuario final, especialmente estudiantes y profesores. Ofrece acceso rápido a cursos, anuncios, chats y entregas, permitiendo interacción constante con el entorno académico. Su estructura utiliza navegación basada en pestañas, pantallas organizadas por rol y consumo directo del backend mediante servicios HTTP.

El **backend**, implementado con Node.js y Express, concentra la lógica completa del sistema. Controla autenticación con JWT, comunicación segura, validación de datos y manejo de todas las colecciones, incluyendo usuarios de distintos tipos, cursos, secciones, grupos, anuncios, chats y entregas. La base de datos está construida sobre MongoDB, con modelos independientes que mantienen cohesión y claridad. Las rutas se encuentran organizadas por módulo para facilitar la mantenibilidad y escalabilidad del código.

---

## **Instalación y Ejecución del Proyecto**

### Aplicación Web (Next.js)

Es necesario ubicarse dentro de la carpeta correspondiente.
Una vez dentro, se instalan las dependencias y puede ejecutarse el servidor de desarrollo:

```
npm install
npm run dev
```

El servicio estará disponible en `http://localhost:3000`.

Variables como credenciales de Firebase o claves de configuración deben colocarse en `.env.local`.

### Aplicación Móvil (React Native / Expo)

Debe abrirse la carpeta móvil y ejecutar los comandos habituales para aplicaciones basadas en Expo:

```
npm install
npx expo start
```

La aplicación puede iniciarse en Android, iOS o el navegador mediante las herramientas que Expo proporciona. Los archivos `.env` permiten configurar la URL del backend y otros valores.

### Backend (Node.js + Express + MongoDB)

Dentro del directorio backend, es necesario instalar dependencias y preparar un archivo `.env` que contenga, al menos:

```
PORT=3000
MONGO_URI=tu_conexion
JWT_SECRET=clave_segura
```

Luego, el servidor puede ejecutarse con:

```
npm install
node app.js
```

El backend quedará accesible en el puerto configurado.

---

## **Funcionamiento del Sistema**

App-Escolar permite que cada rol interactúe con el sistema de manera diferenciada. Los administradores pueden gestionar cursos, secciones, profesores, estudiantes, encargados y grupos académicos, además de publicar anuncios o revisar entregas. Los profesores acceden principalmente a sus cursos, anuncios, chats y entregas asignadas. Los estudiantes reciben comunicación, realizan entregas y revisan contenido relacionado a sus cursos. Los encargados tienen acceso a la información de los estudiantes a su cargo.

El backend garantiza que todas las operaciones estén protegidas por autenticación basada en JWT y que la información esté validada antes de almacenarse. Los modelos independientes permiten preservar la integridad de la estructura académica y facilitan la consulta eficiente. Tanto la aplicación web como la móvil consumen la misma API, lo que mantiene una fuente única de verdad para todos los datos.

---

## **Extensibilidad**

La organización del proyecto permite incorporar módulos adicionales sin alterar la estabilidad del sistema. Entre los componentes que pueden añadirse se encuentran:

* herramientas de evaluación y calificación,
* calendarios académicos,
* reportes institucionales,
* flujos de comunicación interna más avanzados,
* integración con servicios externos.

La estructura modular del backend y la separación por roles en las aplicaciones facilitan la evolución del sistema a futuro.
