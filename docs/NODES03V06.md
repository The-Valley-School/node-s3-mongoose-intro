# Vídeo 06 - Ejercicio API de libros con mongoose, express y mongodb atlas

En este vídeo debes replicar lo que hemos hecho en los vídeos pero en vez de con usuarios, con libros.

Para ello deberás:

- Crear una cuenta en mongo db / mongo atlas y crear una base de datos
- Crear un proyecto node con las librerías básicas (eslint, prettier, husky…)
- Añadir la librería mongoose para conectarte a la API
- Añadir la librería express para poder manejar mejor las rutas
- Añadir la librería dotenv para poder leer variables de entorno.

Una vez tengas las librerías instaladas empieza creado un fichero db.js para conectarte a la API y un seed para llenar la BBDD con libros. Puedes usar estos de ejemplo:

```jsx
const bookList = [
  {
    title: "Harry Potter",
    author: "J.K. Rowling",
    pages: 543,
  },
  {
    title: "1984",
    author: "George Orwell",
    pages: 328,
  },
  {
    title: "To Kill a Mockingbird",
    author: "Harper Lee",
    pages: 281,
  },
  {
    title: "The Great Gatsby",
    author: "F. Scott Fitzgerald",
    pages: 180,
  },
  {
    title: "Pride and Prejudice",
    author: "Jane Austen",
    pages: 279,
  },
];
```

Una vez realizados estos pasos crea los siguientes endpoints:

- GET /book que devolverá la lista de libros
- GET /book/:id que devolverá un libro concreto cuando se indique un ID válido
- GET /book/title/:title que buscará los libros que contengan en su título la palabra indicada
- POST /book que permitirá añadir un libro a la BBDD

Recuerda que el código que hemos visto durante los vídeos puedes encontrarlo en el siguiente repositorio:

<https://github.com/The-Valley-School/node-s3-mongoose-intro>
