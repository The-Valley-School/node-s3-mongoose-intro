# Vídeo 05 - POST para creación y GET con búsqueda

En este vídeo hemos completado nuestra API añadiendo dos métodos:

- GET /user/name/:name que buscará un usuario por nombre
- POST /user que nos permitirá añadir un usuario a nuestra base de datos

Esto es lo que hemos añadido a nuestro fichero index.js:

```jsx
router.get("/user/name/:name", async (req, res) => {
  const name = req.params.name;

  try {
    // Busqueda exacta
    // const user = await User.find({ firstName: name });

    const user = await User.find({ firstName: new RegExp("^" + name.toLowerCase(), "i") });
    if (user?.length) {
      res.json(user);
    } else {
      res.status(404).json([]);
    }
  } catch (error) {
    res.status(500).json(error);
  }
});

// Endpoint de creación de usuarios
router.post("/user", async (req, res) => {
  try {
    const user = new User({
      firstName: req.body.firstName,
      lastName: req.body.lastName,
      phone: req.body.phone,
    });

    const createdUser = await user.save();
    return res.status(201).json(createdUser);
  } catch (error) {
    res.status(500).json(error);
  }
});
```

Puedes observar cómo hemos utilizado el método find de User pero esta vez con async y await e indicándole qué queremos que busque, en este caso un usuario que tenga ese firstName.

Por otro lado, puedes observar también cómo para la creación de usuarios hemos creado un new User y después le hemos ejecutado su método .save para guardarlo en la BBDD.

Recuerda que el código que hemos visto durante los vídeos puedes encontrarlo en el siguiente repositorio:

<https://github.com/The-Valley-School/node-s3-mongoose-intro>
