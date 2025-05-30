# 1. Sarrera

Eustatek 2.000 taula baino gehiago dituen [Datu Bankua](https://eu.eustat.eus/banku/indexArbol.html) kontsultatzeko API bat du martxan.

APIaren helburu nagusia denbora errealean datu estatistikoetarako sarbidea eskaintzea da, datuak berrerabili ahal izateko. Datu horiek analisi edo bistaratze ingurune desberdinetan integratu daiteze erraz, honakoa egiteko, adibidez:

- Web orrietan taula edo grafiko gisa bistaratu, denbora errealean.
- R, Python edo Jupyter Notebooks bezalako tresnetara inportatu, ondoren prozesatu eta aztertzeko.

API honek http **POST** eta **GET** metodoak erabiltzen ditu:

- Datu-bankuko taulen zerrenda bat lortzeko erabiltzen da GET. Metadatuak ere itzultzen ditu, taula zehatz bat kontsultatuz gero.
- Datuak lortzeko, "POST" funtzioa erabili eta kontsulta bat egin **JSON*** (JavaScript Objektuen Notazioa) formatuan. Taula osoa edo haren zatiak eskura ditzakezu.

Jarraian, APIaren sarbide-puntu bakoitza (endpointak) zehazten da.


# 2. Datu-bankuko taulen zerrenda

GET funtzioa datu-bankuaren url gainean erabiltzen baduzu, taula guztien zerrenda JSON formatuan agertuko da. Datu-bankuaren URL helbideak egitura hau du:

`https://www.eustat.eus/bankupx/api/v1/{lang}/DB`

`{lang}` parametroa hizkuntzari dagokio. Nahitaezkoa da eta balio hauek har ditzake: EU:euskara / ES:gaztelania / EN:ingelesa.

Taulen zerrenda euskeraz:

[https://www.eustat.eus/bankupx/api/v1/eu/DB] (https://www.eustat.eus/bankupx/api/v1/eu/DB)

Erantzunaren itxura:

```json
{
    "id": "PX__fe_inem06.px",
    "type": "t",
    "text": "Euskal AEko erregistratutako langabezia, lurralde eremuaren eta sexuaren arabera. 1997 - 2022",
    "updated": "2023-01-09T15:04:41"
  },
  {
    "id": "PX__feinem_inem06.px",
    "type": "t",
    "text": "Euskal AEko erregistratutako langabezia, lurralde eremuaren eta sexuaren arabera",
    "updated": "2021-02-17T10:04:22"
  }
```

JSON formatuan azaltzen den erantzunak informazio hau dakar:

| Campo     | Deskribapena                                                                                          |
|-----------|-------------------------------------------------------------------------------------------------------|
| `id`      | Taularen kode identifikatzailea                                                                       |
| `type`    | `t` = Taula                                                                                           |
| `text`    | Taularen izenburua (edukiaren deskribapena + denbora-tartea)                                          |
| `updated` | Taula azken aldiz eguneratu den eguna    


# 3. Taula baten metadatuak

Taula baten URLaren gaineko GET funtzioak taulako metadatuak itzuliko ditu JSON formatuan. Taularen identifikazio kodea ezagutzen baduzu, URLa kontsulta dezakezu parametro hauekin:

`https://www.eustat.eus/bankupx/api/v1/{lang}/DB/[id]`

`{lang}` eremua hizkuntzari dagokio, eta `[id]` eremua taularen identifikatzaileari dagokio, interesatzen zaizun datu edo metadatuekin.

Metadatuek izenburu bat dute ("title") eta taulako aldagai zerrenda bat.

Adibidea:

👉(https://www.eustat.eus/bankupx/api/v1/eu/DB/PX_050403_cpra_tab_a_25.px)

Erantzunaren itxura:

```json
{
  "title": "Euskal AEko 16 urte eta gehiagoko biztanleria landunaren asteko orduen batez bestekoa, lurralde, sexu, sektore ekonomiko eta hiruhilekoaren arabera (orduak). 2015 - 2025",
  "variables": [
    {
      "code": "territorio histórico",
      "text": "lurralde historikoa",
      "values": [
        "_T",
        "01",
        "48",
        "20"
      ],
      "valueTexts": [
        "Euskal AE",
        "Araba/Álava",
        "Bizkaia",
        "Gipuzkoa"
      ]
    },
    {
      "code": "sexo",
      "text": "sexua",
      "values": [
        "_T",
        "1",
        "2"
      ],
      "valueTexts": [
        "Guztira",
        "Gizona",
        "Emakumea"
      ]
    },
    {
      "code": "sector económico",
      "text": "sektore ekonomikoa",
      "values": [
        "_T",
        "01",
        "02",
        "03",
        "04"
      ],
      "valueTexts": [
        "Guztira",
        "Nekazaritza, abeltzaintza, basozaintza eta arrantza",
        "Industria",
        "Eraikuntza",
        "Zerbitzuak"
      ]
    },
    {
      "code": "trimestre",
      "text": "hiruhilekoa",
      "values": [
        "10",
        "20",
        "30",
        "40",
        "50"
      ],
      "valueTexts": [
        "Urteko batez bestekoa",
        "1. Hiruhilekoa",
        "2. Hiruhilekoa",
        "3. Hiruhilekoa",
        "4. Hiruhilekoa"
      ]
    },
    {
      "code": "periodo",
      "text": "aldia",
      "values": [
        "2015",
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
        "2015",
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
```

"Variables" objetuek lau atributu dituzte:

| Campo       | Descripción                                          |
|-------------|------------------------------------------------------|
| `code`      | Aldagaiaren kodea                                    |
| `text`      | Aldagaiaren izena                                    |
| `values`    | Aldagaiaren balioen zerrenda, kodean                 |
| `valueTexts`| Aldagaiaren balioen zerrenda, testuan                |


# 4. Taula bateko datuak

Taula bateko datuak lortzeko, kontsulta bat egin behar diozu JSON formatuan, interesatzen zaizun taularen URLari. Metadatuak lortzeko erabiltzen den sarbide-puntu bera da, baina oraingoan "POST" funtzioa erabiltzen da.

Kontsulta guztiak honako testu honekin hasten dira:  `{query: [{...}]}`. Honako iragazki hauek erabiltzen dira:

| Filtroa | Describapena                                                                |
|--------|------------------------------------------------------------------------------|
| `item` | Iragazi nahi diren banakako balioen hautaketa                                                             |
| `top`  | Lortu nahi diren azken "x" balioen kopurua hautatzeko. Normalean, aldia/urtea aldagaiarekin erabiltzen da |

Adibidez:

```json
{
  "query": [
    {
      "code": "componente",
      "selection": {
        "filter": "item",     // ← "componente" izeneko aldagaiaren filtroa
        "values": [
          "200"               // ← aukeratutako balioa
        ]
      }
    },
    {
      "code": "tipo de serie",
      "selection": {
        "filter": "item",     // ←  "tipo de serie" izeneko aldagaiaren filtroa
        "values": [
          "10",               // ← aukeratutako balioak
          "30"
        ]
      }
    },
    {
      "code": "periodo",
      "selection": {
        "filter": "top",      // ←  "top" filtroa, "periodo" izeneko aldagaiaren azken "x" baloreak lortzeko
        "values": [5]         // ← azken 5 baloreak eskatzen dira
      }
    }
  ],
  "response": {
    "format": "json-stat"     // ← irteerako formatua (json-stat dago lehenetsia)
  }
}
```
Kontsulta hori egiteko, taulak zer aldagai eta balio dituen jakin behar da. Taula bakoitzaren aldagai eta balioen informazioa bi modutara lor daiteke:

- Metadatuak kontsultatuz, 3 atalean adierazten den bezala **3. Taula baten metadatuak**.
- Datu-bankuko aldagaiak eta balioak hautatzeko laguntzailea (erabiltzailearen interfazea) erabiliz. Taula bateko hautaketa-laguntzailearen URL helbideak egitura hau du:

`https://www.eustat.eus/bankupx/pxweb/{lang}/DB/-/{id}`

Jarraian, hautaketa-laguntzailea erabiliz POST kontsulta konfiguratzeko beharrezko urratsak azalduko ditugu:


### Ejemplo de selección de variables y valores

Queremos seleccionar algunos valores concretos de la tabla "Producto interior bruto (PIB) de la C.A. de Euskadi (oferta) por territorio histórico, rama de actividad (A-38), tipo de dato y de medida. 1995 - 2023" que se encuentra en la dirección https://es.eustat.eus/bankupx/pxweb/es/DB/-/PX_170112_cpib_pib_a_01.px.

![Selección de variables y valores](../img/PIB_seleccion.PNG)

Haz clic en el apartado **“Disponer de esta tabla en su aplicación”**. Esto mostrará la URL y la consulta necesarias para obtener los datos mediante la API.

![Consulta JSON generada](../img/PIB_consulta.PNG)

La interfaz ayuda al usuario a generar y editar el código que se utilizará en la API. Está pensada para generar el código de las consultas y no para su uso en producción.

Para leer los archivos JSON de salida de las solicitudes de datos descritas en esta página, debe utilizarse un programa o lenguaje de programación que permita procesar este formato. Se han elaborado tutoriales y ejemplos de código en  [**R**](../code_examples/tutorial_R_es.Rmd), [**Python**](../code_examples/tutorial_Python_es.ipynb) y [**JavaScript**](../code_examples/tutorial_highcharts_es.md) para facilitar a los usuarios el uso de la API de Eustat.

### Formatos de salida

La API puede devolver resultados en 5 formatos diferentes:

- **JSON-stat**, versión 1.2 *(formato predeterminado)*
- **CSV** (formato plano)
- **CSV2** (formato compatible con tablas dinámicas)
- **CSV3** (igual que CSV2, pero con códigos en lugar de texto)
- **XLSX** (Excel)

Para un tratamiento flexible de los datos, recomendamos JSON-stat, que es la salida por defecto.

