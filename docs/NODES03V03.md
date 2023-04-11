# Vídeo 03 - Seeds, schemas y modelos de mongoose

En Mongoose, los esquemas y modelos son conceptos importantes que se utilizan para definir la estructura de los datos y la forma en que se almacenan en la base de datos.

Un esquema en Mongoose es un objeto que define la estructura de los datos que se almacenan en una colección de MongoDB. El esquema describe los campos o propiedades de los datos, incluyendo su tipo de datos, la validación y las opciones de configuración. Por ejemplo, un esquema para una colección de usuarios podría incluir campos como nombre, correo electrónico y contraseña, junto con las opciones de configuración para cada campo.

Un modelo en Mongoose es una clase que se crea a partir de un esquema y proporciona una interfaz para interactuar con la base de datos MongoDB. El modelo se utiliza para realizar operaciones como crear, leer, actualizar y eliminar documentos en la base de datos. Por ejemplo, si tienes un modelo de usuarios en Mongoose, puedes utilizarlo para crear un nuevo usuario en la base de datos mediante el método create(), o para buscar usuarios existentes mediante el método find().

Para empezar a trabajar con nuestra base de datos de usuarios hemos creado nuestro esquema y nuestro modelo User en /models/User.js:

```jsx
const mongoose = require("mongoose");
const Schema = mongoose.Schema;

// Creamos el schema del usuario
const userSchema = new Schema(
  {
    firstName: {
      type: String,
      required: true,
    },
    lastName: {
      type: String,
      required: true,
    },
    phone: {
      type: Number,
      required: false,
    },
  },
  {
    timestamps: true,
  }
);

const User = mongoose.model("User", userSchema);
module.exports = { User };
```

Ahora lo vamos a utilizar para crear un seed. Un "seed" es a un proceso mediante el cual se insertan datos de prueba o de ejemplo en una base de datos.

El proceso de siembra (o "seeding") es comúnmente utilizado para llenar una base de datos con datos iniciales que permitan probar y validar su funcionamiento. Esto puede incluir la creación de registros de usuarios, productos, pedidos, etc., con datos que reflejen casos de uso típicos del sistema.

Nuestro fichero /seeds/user.seed.js ha quedado así:

```jsx
const mongoose = require("mongoose");
const { connect } = require("../db.js");
const { User } = require("../models/User.js");

const userList = [
  {
    firstName: "Fran",
    lastName: "Linde",
    phone: 123123123,
  },
  {
    firstName: "Edu",
    lastName: "Cuadrado",
  },
  {
    firstName: "Gon",
    lastName: "Fernández",
    phone: 666777888,
  },
];

connect().then(() => {
  console.log("Tenemos conexión");

  // Borrar datos
  User.collection.drop().then(() => {
    console.log("Usuarios eliminados");

    // Añadimos usuarios
    const documents = userList.map((user) => new User(user));
    User.insertMany(documents)
      .then(() => console.log("Datos guardados correctamente!"))
      .catch((error) => console.error(error))
      .finally(() => mongoose.disconnect());
  });
});
```

Y para ejecutarlo hemos creado un script en el package.json:

```jsx
"seed:users": "node ./seeds/user.seed.js",
```
