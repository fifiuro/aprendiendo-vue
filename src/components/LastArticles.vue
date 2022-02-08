<template>
  <div id="general">
    <Slider
      texto="Bienvenido al Curso de Vue con Victor Robles de victorroblesweb.es"
      home="true"
    ></Slider>
    <div class="center">
      <section id="content">
        <h2 class="subheader">Últimos artículos</h2>

        <!--Listado articulos-->
        <div id="articles">
          <article class="article-item" id="article-template">
            <div class="image-wrap">
              <img
                src="https://www.xtrafondos.com/wallpapers/resized/paisaje-digital-en-atardecer-5846.jpg?s=large"
                alt="Paisaje"
              />
            </div>

            <h2>Articulo de prueba</h2>
            <span class="date"> Hace 5 minutos </span>
            <a href="#">Leer más</a>

            <div class="clearfix"></div>
          </article>

          <!--AÑADIR ARTICULOS VIA JS-->
        </div>
      </section>
      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>

<script>
import Slider from "./Slider.vue";
import Sidebar from "./Siderbar.vue";

export default {
  name: "LastArticles",
  components: {
    Slider,
    Sidebar,
  },
};
</script>