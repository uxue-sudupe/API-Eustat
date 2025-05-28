# API-Eustat
Eustaten APIaren dokumentazioa eta tutorialak / Documentación y tutoriales de la API de Eustat       ➡️ [Irakurri gaztelaniaz / Leer en castellano](#documentación-en-castellano)

## 📘 **1. Eustaten APIaren gida**
[Eustaten APIaren gida teknikoak](doc/API_doc_eu.md) APIaren sarbide-puntuak (endpointak) identifikatzen ditu eta datuetara sartzeko modua deskribatzen du.

---

## 🧭 2. Swagger bisorea (Open API estandarrean)

APIaren esplorazio eta proba interaktiboa errazteko, [**Swagger UI** bisore bat](swagger/eu/index.html) gehitu da. Nabigatzailetik bertatik dokumentazioa kontsultatu eta eskaerak egin daitezke.

---

# 📚 APIaren erabilerarako tutorialak

Errepositorio honek Eustaten APIaren erabilera ikasteko hiru tutorial praktiko biltzen ditu. **R** eta **Python** erabiliz, APIari kontsultak nola egin eta datuak nola prozesatu erakusten dute.

### ✅ Eskuragarri dauden tutorialak

1. 📘 [R-n egindako tutoriala (RMarkdown)](Tutorial_API_Eustat_R.Rmd)  
2. 📗 [R-n egindako tutoriala (Jupyter Notebook)](Tutorial_API_Eustat_R.ipynb)  
3. 📙 [Python-en egindako tutoriala (Jupyter Notebook)](Tutorial_API_Eustat_Python.ipynb)
4.  📊 Javascript-en adibide bat, API dei bat eginez nola sortu daitekeen Higcharts grafiko bat

---

## 📄 OpenAPI Espezifikazioa

APIaren definizioa [`descriptor.yaml`](./descriptor.yaml) fitxategian dago, **OpenAPI 3.0** estandarraren egiturari jarraituz.

Espezifikazio honek honako hauek deskribatzen ditu:

- ✅ Eskuragarri dauden endpoint-ak  
- 🔁 Onartutako HTTP metodoak  
- 📥 Sarrerako eta irteerako parametroak  
- 🧾 Erantzun-kodeak  
- 🧪 Erabilera-adibideak

  ---

# 📊 Documentación en castellano

Este repositorio contiene la documentación técnica de la API de Eustat conforme al estándar **OpenAPI 3.0**, lo que facilita su integración, comprensión y mantenimiento.

🔗 **Acceso directo a la documentación:**  
[https://uxue-sudupe.github.io/openapi-eustat](https://uxue-sudupe.github.io/openapi-eustat)

---

## 📄 Especificación OpenAPI

La definición de la API se encuentra en el archivo [`descriptor.yaml`](./descriptor.yaml), estructurada según el estándar **OpenAPI 3.0**.

Esta especificación incluye:

- ✅ Endpoints disponibles  
- 🔁 Métodos HTTP permitidos  
- 📥 Parámetros de entrada y salida  
- 🧾 Códigos de respuesta  
- 🧪 Ejemplos de uso

---

## 🧭 Visor Swagger UI

Para facilitar la exploración y prueba de la API, se incluye un visor interactivo **Swagger UI**. Desde aquí puedes consultar la documentación y realizar peticiones directamente desde el navegador.

🌐 **Accede al visor Swagger:**  
[https://uxue-sudupe.github.io/openapi-eustat/open_api.html](https://uxue-sudupe.github.io/openapi-eustat/open_api.html)

---

# 📚 Tutoriales de uso

Este repositorio incluye tres tutoriales prácticos que te guiarán en el uso de la API de Eustat. Están disponibles en **R** y **Python** e incluyen ejemplos de consulta y tratamiento de datos.

### ✅ Tutoriales disponibles

1. 📘 [Tutorial en R (RMarkdown)](Tutorial_API_Eustat_R.Rmd)  
2. 📗 [Tutorial en R (Jupyter Notebook)](Tutorial_API_Eustat_R.ipynb)  
3. 📙 [Tutorial en Python (Jupyter Notebook)](Tutorial_API_Eustat_Python.ipynb)
