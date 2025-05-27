# 1. Introducción

Eustat ofrece una API para consultas a las más de 2.000 tablas de su [Banco de Datos](https://www.eustat.eus/banku/indexArbol.html).

Esta API utiliza los métodos HTTP **POST** y **GET**:

- `GET` se usa para obtener un listado de las tablas del banco de datos. También devuelve los metadatos, en el caso de consultar una tabla concreta.
- Para obtener datos, debes usar la función `POST` y formular una consulta en **JSON** (Notación de Objetos JavaScript). Puedes obtener la tabla completa o partes de ella.


# 2. Listado de tablas del banco de datos

Si usas la función GET sobre la url del banco de datos, se muestra el listado de todas las tablas en formato JSON:

👉 [https://www.eustat.eus/bankupx/api/v1/es/DB](https://www.eustat.eus/bankupx/api/v1/es/DB)

Aspecto de la respuesta:

```json
[
  {
    "id": "PX__fe_inem06.px",
    "type": "t",
    "text": "Paro registrado de la C.A. de Euskadi por ámbitos territoriales y sexo. 1997 - 2022",
    "updated": "2023-01-09T15:04:41"
  },
  {
    "id": "PX__feinem_inem06.px",
    "type": "t",
    "text": "Paro registrado de la C.A. de Euskadi por ámbitos territoriales y sexo",
    "updated": "2021-02-17T10:04:22"
  }
]
```

El texto JSON que se muestra contiene los siguientes campos:

| Campo     | Descripción                                                                                           |
|-----------|-------------------------------------------------------------------------------------------------------|
| `id`      | Código identificativo de la tabla                                                                     |
| `type`    | `t` = Tabla                                                                                           |
| `text`    | Título de la tabla (descripción del contenido + intervalo de tiempo)                                  |
| `updated` | Fecha de última actualización de la tabla    

# 3. Metadatos de una tabla

La función GET sobre la URL de una tabla devolverá los metadatos de la tabla en formato JSON. Si conoces el código identificativo de la tabla en el banco de datos, puedes usar la URL con estos parámetros:

https://www.eustat.eus/bankupx/api/v1/{lang}/DB/[id]

El campo {lang} se corresponde con el idioma. Es obligatorio y puede tomar los siguientes valores: ES: español / EU: euskera / EN: inglés.

El campo [id] es opcional y corresponde al identificador de la tabla con los datos o metadatos de interés.

Los metadatos constan de un título ("title") y una lista de variables para la tabla.

Ejemplo:

👉[https://www.eustat.eus/bankupx/api/v1/es/DB/PX_132680_cetr_etr04t.px]

Aspecto de la respuesta:

```json
{
  "title": "Entradas, pernoctaciones y grado de ocupación en establecimientos turísticos receptores* de la C.A. de Euskadi, por variable, territorio histórico, origen y período. Semana Santa. 2016 - 2025",
  "variables": [
    {
      "code": "variable",
      "text": "variable",
      "values": [
        "10",
        "20",
        "30"
      ],
      "valueTexts": [
        "Entradas",
        "Pernoctaciones",
        "Grado de ocupación por plazas"
      ]
    },
    {
      "code": "territorio histórico",
      "text": "territorio histórico",
      "values": [
        "00",
        "01",
        "48",
        "20"
      ],
      "valueTexts": [
        "C.A. de Euskadi",
        "Araba/Álava",
        "Bizkaia",
        "Gipuzkoa"
      ]
    },
    {
      "code": "origen",
      "text": "origen",
      "values": [
        "10",
        "20",
        "30"
      ],
      "valueTexts": [
        "Total",
        "-Estado",
        "-Extranjero"
      ]
    },
    {
      "code": "periodo",
      "text": "periodo",
      "values": [
        "2016",
        "2017",
        "2018",
        "2019",
        "2020",
        "2021",
        "2022",
        "2023",
        "2024",
        "2025"
      ],
      "valueTexts": [
        "2016",
        "2017",
        "2018",
        "2019",
        "2020",
        "2021",
        "2022",
        "2023",
        "2024",
        "2025"
      ],
      "time": true
    }
  ]
}
```

 Los objetos "variables" tienen cuatro atributos:

| Campo       | Descripción                                                |
|-------------|------------------------------------------------------------|
| `code`      | Código de la variable                                      |
| `text`      | Nombre de la variable                                      |
| `values`    | Listado de valores de la variable, en código               |
| `valueTexts`| Listado de valores de la variable, en texto                |


# 4. Datos de una tabla

Para formular las consultas en formato JSON, se puede usar la interfaz de usuario del banco de datos, y seleccionar las variables y valores de interés en la página correspondiente a la tabla.


Haga clic en el apartado “Disponer de esta tabla en su aplicación”. Esto le brindará información sobre la URL y la consulta que debe enviar para recoger los datos con la API.

