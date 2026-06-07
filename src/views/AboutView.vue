<template>
  <div class="container my-5">
    <div class="row align-items-center">
      <div class="col-12 col-md-6 mb-4 mb-md-0 text-center">
        <img :src="zonasClimas" class="img-fluid rounded shadow" width="500" alt="Clima en Chile" />
      </div>

      <div class="col-12 col-md-6">
        <h1 class="heading heading--primary">Sobre esta Web y Algunos Detalles</h1>

        <p class="heading heading--secondary">
          Esta Web muestra el clima en algunas ciudades de Chile. Las temperaturas son obtenidas
          mediante la API
          <a href="https://open-meteo.com" target="_blank">Open-Meteo</a>.
        </p>

        <p>
          <strong>Clima Árido:</strong> se extiende desde Arica a La Serena, se caracteriza por
          recibir una alta radiación solar con una T° de 18°C, aire extremadamente seco y casi total
          ausencia de precipitaciones. Esto impide el desarrollo de vegetación y por lo tanto
          determina un paisaje desértico.
        </p>

        <p>
          <strong>Clima Semi Árido:</strong> conocido como clima de Estepa seca, entre La Serena y
          el norte de Santiago, caracterizado por presencia de precipitaciones ocasionales y una
          temperatura media más baja que la anterior. Permiten la existencia de formaciones
          vegetales de tipo xerófilo (adaptados a la aridez) y vegetación esclerófila (hojas duras y
          espinas).
        </p>

        <p>
          <strong>Clima Templado:</strong> Clima Templado: es el más extendido a lo largo de Chile,
          con condiciones óptimas para el desarrollo de alta diversidad de formaciones vegetales.
          Sus variaciones se dividen en tres: Clima Templado Mediterráneo (desde el Valle del Maipo
          a Concepción), con la presencia de bosque esclerófilo en la zona central; Templado
          lluvioso (de Concepción a Puerto Montt); y Templado Marítimo (desde Puerto Montt a
          Coyhaique).
        </p>

        <p>
          <strong>Clima Frío:</strong> entre Coyhaique y Punta Arenas, caracterizado por una
          reducción de las precipitaciones (350 mm) y T° medias de 4 y 5º C, con fuertes vientos que
          condicionan la presencia de bosques subantárticos de lenga y estepa o pampa patagónica.
        </p>
      </div>
    </div>
  </div>
</template>
<script setup>
import zonasClimas from '@/assets/img/zonasyclimas.jpg'
</script>
<style scoped>
.heading--primary {
  color: white;
  text-shadow: 6px 6px 11px #000000;
}

.heading--secondary {
  color: white;
  text-shadow: 2px 2px 6px #000000;
  font-size: 3vh;
}
</style>
