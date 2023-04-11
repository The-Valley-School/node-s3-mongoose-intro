# Vídeo 04 - GET de usuarios con schema, listado e individual

En este vídeo hemos visto cómo podemos hacer un GET de la lista de usuarios que tenemos en nuestro MongoDB.

Para hacer nuestra API hemos utilizado express y hemos dejado el fichero index.js de la siguiente manera:

```jsx
const express = require("express");

// Conexión a la BBDD
const { connect } = require("./db.js");
connect();

// Modelos
const { User } = require("./models/User.js");

// Creamos router de expres
const PORT = 3000;
const server = express();
const router = express.Router();

// Configuración del server
server.use(express.json());
server.use(express.urlencoded({ extended: false }));

// Rutas
router.get("/", (req, res) => {
  res.send("Esta es la home de nuestra API");
});

router.get("/user", (req, res) => {
  User.find()
    .then((users) => res.json(users))
    .catch((error) => res.status(500).json(error));
});

router.get("/user/:id", (req, res) => {
  const id = req.params.id;

  User.findById(id)
    .then((user) => {
      if (user) {
        res.json(user);
      } else {
        res.status(404).json({});
      }
    })
    .catch((error) => res.status(500).json(error));
});

server.use("/", router);
server.listen(PORT, () => {
  console.log(`Server levantado en el puerto ${PORT}`);
});
```

Fíjate que para realizar la búsqueda en la API y recuperar todos los usuarios hemos usado el modelo User:

```jsx
User.find()
  .then((users) => res.json(users))
  .catch((error) => res.status(500).json(error));
```

Y para recuperar un usuario concreto hemos usado findById:

```jsx
User.findById(id)
  .then((user) => {
    if (user) {
      res.json(user);
    } else {
      res.status(404).json({});
    }
  })
  .catch((error) => res.status(500).json(error));
```

Por otro lado hemos modificado el fichero db.js añadiendo el parámetro dbName para indicar exactamente a qué base de datos queremos que se conecte, en nuestro caso la hemos llamado node-s3:

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
  dbName: "node-s3",
};

const connect = async () => {
  const database = await mongoose.connect(DB_CONNECTION, config);
  const name = database.connection.name;
  const host = database.connection.host;
  console.log(`Conectado a la base de datos ${name} en el host ${host}`);
};

module.exports = { connect };
```
