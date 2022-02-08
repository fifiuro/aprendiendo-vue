<template>
  <div id="general">
    <Slider texto="Pagina de Pruebas"></Slider>
    <div class="center">
      <section id="content">
        <h2 class="subheader">Pagina de Pruebas</h2>
        <h3>{{ id_desde_url }}</h3>
        <h4>El nombre es: {{ nombre }}</h4>
        <button @click="actualizarNombre()">Actualizar nombre</button>
        <button @click="redirigirAlBlog()">Redirigir al Blog</button>
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
  name: "Pagina",
  components: {
    Slider,
    Sidebar,
  },
  created() {
    console.log("Componente creado...");
  },
  mounted() {
    this.id_desde_url = this.$route.params.id;
    console.log("Componente montado...");
  },
  updated() {
    console.log("Componente actualizado...");
  },
  destroyed() {
    console.log("Componente eliminado...");
  },
  data() {
    return {
      id_desde_url: null,
      nombre: "Christian Rene",
    };
  },
  methods: {
    actualizarNombre() {
      this.nombre = "CHRISTIAN RENE";
      console.log(this.nombre);
    },
    redirigirAlBlog() {
      this.$router.push("/blog");
    },
  },
};
</script>