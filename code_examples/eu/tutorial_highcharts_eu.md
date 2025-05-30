# Visualización de la tasa de paro en Euskadi con Highcharts

Este tutorial muestra cómo utilizar la **API PXStat de Eustat** para obtener la tasa de paro en Euskadi y representarla mediante un gráfico con **Highcharts**.

> **Nota:** Highcharts es gratuito solo para uso no comercial. Si lo quieres usar en publicaciones institucionales o productos, consulta su [licencia](http://www.highcharts.com/products/highcharts).

---

## 1. Crear un HTML mínimo para Highcharts

```html
<!DOCTYPE html>
<html lang="es">
<head>
  <meta charset="UTF-8">
  <title>Paro en Euskadi</title>
  <script src="https://code.highcharts.com/highcharts.js"></script>
  <script src="https://code.jquery.com/jquery-3.6.0.min.js"></script>
</head>
<body>
  <div id="paro-chart" style="height: 500px; width: 100%;"></div>
</body>
</html>
```

---

## 2. Llamar a la API PXStat de Eustat para obtener solo Euskadi

En este ejemplo hacemos una petición `POST` a la API para obtener solo los datos del ámbito `00001` (Euskadi):

```js
fetch("https://www.eustat.eus/bankupx/api/v1/es/DB/PX_050407_cempa_empa_pp41.px", {
  method: "POST",
  headers: { "Content-Type": "application/json" },
  body: JSON.stringify({
    query: [
      {
        code: "\u00e1mbitos territoriales",
        selection: { filter: "item", values: ["00001"] }
      }
    ]
  })
})
.then(res => res.json())
.then(json => {
  // Procesamiento de datos aquí
});
```

---

## 3. Transformar los datos para Highcharts
