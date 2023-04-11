# Vídeo 02 - Conexión a la BBDD con mongoose y dotenv

Para conectarnos desde Node a nuestra base de datos Mongo, podemos usar la librería nativa la cual nos obligará a hacer consultas de una manera muy manual:

<https://github.com/mongodb/node-mongodb-native>

O bien una librería más avanzada como es Mongoose:

<https://github.com/Automattic/mongoose>

Mongoose ofrece una capa de abstracción que nos permite trabajar de una manera más cómoda con MongoDB, ya que incluye un ODM (Object Document Mapping).

Para instalar mongoose basta con ejecutar:

```jsx
npm install mongoose --save
```

Tras esto vamos a crear un fichero db.js que realice la conexión con nuestra base de datos en MongoDB o Mongo Atlas:

```jsx
// Cargamos variables de entorno
require("dotenv").config();
const DB_CONNECTION = process.env.DB_URL;

const mongoose = require("mongoose");

// Configuración de la conexión
const config = {
  useNewUrlParser: true,
  useUnifiedTopology: true,
  serverSelectionTimeoutMS: 5000,
};

const connect = async () => {
  const database = await mongoose.connect(DB_CONNECTION, config);
  const name = database.connection.name;
  const host = database.connection.host;
  console.log(`Conectado a la base de datos ${name} en el host ${host}`);
};

module.exports = { connect };
```

Puedes observar como la URL de conexión la estamos leyendo desde una variable de entorno que declaramos en un fichero .env

Para leer variables de entorno hemos instalado la librería dotenv que nos facilita leer estos ficheros, para instalar dotenv debemos ejecutar:

```jsx
npm install dotenv --save
```

Y de esta manera leeremos nuestro fichero .env donde tendremos la URL de conexión de MongoDB que hemos sacado de la página web.

Esta URL es única para cada instalación de MongoDB, así que no copies esta URL de ejemplo, recuerda utilizar la que te ofrezca tu base de datos e indica la contraseña de tu usuario.

```jsx
DB_URL = "mongodb+srv://franlindebl:<USER_PASSWORD>@franlindebl-cluster.y4849ob.mongodb.net/?retryWrites=true&w=majority";
```

Ahora ya desde nuestro fichero index.js podemos realizar la conexión con la base de datos:

```jsx
// Conexión a la BBDD
const { connect } = require("./db.js");
connect();
```
