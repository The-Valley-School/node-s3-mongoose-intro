# Vídeo 01 - Intro de BBDD relacionales y no relacionales

Una base de datos es un conjunto organizado de datos relacionados entre sí, que se almacenan en un dispositivo de almacenamiento, como un disco duro o una memoria. Las bases de datos permiten a los usuarios guardar, recuperar, modificar y eliminar datos de manera eficiente y segura.

Las bases de datos se utilizan en una amplia variedad de aplicaciones, como sistemas de gestión de inventarios, sistemas de gestión de recursos humanos, sistemas de gestión de ventas, sistemas de gestión de bibliotecas, entre otros. También se utilizan en aplicaciones web y móviles para almacenar y gestionar datos de usuarios, productos, servicios, etc.

Las bases de datos pueden ser clasificadas en diferentes tipos, como bases de datos relacionales, bases de datos no relacionales (también conocidas como bases de datos NoSQL), bases de datos espaciales, bases de datos temporales, entre otras. Cada tipo de base de datos tiene sus propias características y se utiliza para diferentes tipos de aplicaciones.

**Relacionales vs NO relacionales**

Las bases de datos relacionales y no relacionales son diferentes en varios aspectos, tales como:

- **Estructura de datos:** Las bases de datos relacionales tienen una estructura de datos tabular, donde la información se almacena en tablas con filas y columnas. Por otro lado, las bases de datos no relacionales tienen una estructura de datos más flexible, como documentos, gráficos, pares clave-valor, entre otros.
- **Modelo de datos:** Las bases de datos relacionales utilizan el modelo relacional, que se basa en la teoría de conjuntos y relaciones matemáticas. Por otro lado, las bases de datos no relacionales utilizan diferentes modelos de datos, como el modelo de documentos, el modelo de grafo, el modelo clave-valor, entre otros.
- **Escalabilidad:** Las bases de datos no relacionales suelen ser más escalables que las bases de datos relacionales, especialmente en entornos de grandes volúmenes de datos y alta concurrencia.
- **Transacciones:** Las bases de datos relacionales son conocidas por su soporte a transacciones ACID (Atomicidad, Consistencia, Aislamiento y Durabilidad), que garantizan que las operaciones se completen correctamente o se deshagan en caso de un error. Por otro lado, las bases de datos no relacionales pueden tener diferentes niveles de soporte a transacciones y pueden utilizar diferentes enfoques, como transacciones distribuidas o eventualmente consistentes.
- **Consultas y análisis:** Las bases de datos relacionales tienen un lenguaje de consulta estructurado (SQL) que se utiliza para realizar consultas y análisis de datos. Por otro lado, las bases de datos no relacionales pueden tener diferentes enfoques para consultas y análisis, como lenguajes de consulta propios o integración con herramientas de análisis de datos.

**Ejemplo de Base de datos relacional, por ejemplo SQL:**

Tabla de usuarios:

| ID  | Nombre | Apellido  | Edad | Vehiculo_ID |
| --- | ------ | --------- | ---- | ----------- |
| 1   | Juan   | Perez     | 30   | 1           |
| 2   | Maria  | Rodriguez | 25   | NULL        |
| 3   | Pedro  | Sanchez   | 40   | 2           |

Tabla de vehículos:

| ID  | Marca  | Modelo  | Año  |
| --- | ------ | ------- | ---- |
| 1   | Toyota | Corolla | 2010 |
| 2   | Ford   | Mustang | 2015 |

En este caso, la tabla de usuarios tiene una columna llamada "Vehiculo_ID" que se relaciona con la tabla de vehículos. Esto permite establecer una relación entre un usuario y su vehículo correspondiente.

**Ejemplo de base de datos no relacional, por ejemplo MongoDB:**

Documento con todos los datos:

```jsx
{
  "usuarios": [
    {
      "ID": 1,
      "nombre": "Juan",
      "apellido": "Perez",
      "edad": 30,
      "vehiculo": {
        "ID": 1,
        "marca": "Toyota",
        "modelo": "Corolla",
        "año": 2010
      }
    },
    {
      "ID": 2,
      "nombre": "Maria",
      "apellido": "Rodriguez",
      "edad": 25,
      "vehiculo": null
    },
    {
      "ID": 3,
      "nombre": "Pedro",
      "apellido": "Sanchez",
      "edad": 40,
      "vehiculo": {
        "ID": 2,
        "marca": "Ford",
        "modelo": "Mustang",
        "año": 2015
      }
    }
  ]
}
```

En este caso, los usuarios y sus vehículos se almacenan en un documento JSON anidado. Cada objeto de usuario tiene una propiedad llamada "vehiculo" que puede ser nula si el usuario no tiene vehículo.

Tras hablar un poco de las diferentes bases de datos, hemos hablado de MongoDB, la base de datos no relacional más usada:

<https://www.mongodb.com/>

Para usar mongo se puede instalar en el equipo:

<https://www.mongodb.com/docs/manual/installation/>

Se puede una un contenedor o máquina virtual con docker:

<https://www.mongodb.com/compatibility/docker>

O la manera más cómoda, se puede hacer uso de un sistema en la nube:

<https://www.mongodb.com/cloud/atlas/register>

Esta última será la que usemos nosotros.
