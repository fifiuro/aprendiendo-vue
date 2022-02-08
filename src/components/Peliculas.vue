<template>
  <div id="general">
    <div class="center">
      <section id="content">
        <h1 class="subheader">Peliculas</h1>

        <div class="mis-datos" v-if="misDatos">
          {{ misDatos }}
          <p v-html="misDatos"></p>
          <br>
          {{web | mayusculas | concatenaYear('ESTE ES EL MEJOR ANIO')}}
        </div>

        <div class="favorita" v-if="favorita">
          La pelicula marcada es:
          <h3>{{ favorita.title }}</h3>
        </div>

        <!-- Listado de Peliculas -->
        <div id="articles">
          <div
            v-for="pelicula in peliculasMayuscula"
            v-bind:key="pelicula.title"
          >
            <Pelicula
              :pelicula="pelicula"
              v-on:favorita="haLlegadoLaPeliculaFavorita"
              @favorita="haLlegadoLaPeliculaFavorita"
            ></Pelicula>
          </div>
        </div>
      </section>
      <Sidebar></Sidebar>
      <div class="clearfix"></div>
    </div>
  </div>
</template>

<script>
import Sidebar from "./Siderbar.vue";
import Pelicula from "./Pelicula.vue";

export default {
  name: "Peliculas",
  components: {
    Pelicula,
    Sidebar,
  },
  filters: {
    mayusculas(value) {
      return value.toUpperCase();
    },
    concatenaYear(value, message) {
      var date = new Date();

      return value + ' ' + date.getFullYear() + ' ' + message;
    }
  },
  methods: {
    haLlegadoLaPeliculaFavorita(favorita) {
      console.log(favorita);
      alert("Se ha ejecutado el evento en el padre");
      this.favorita = favorita;
    },
  },
  computed: {
    peliculasMayuscula() {
      var peliculasMod = this.peliculas;
      for (var i = 0; i < peliculasMod.length; i++) {
        peliculasMod[i].title = peliculasMod[0].title.toUpperCase();
      }

      return peliculasMod;
    },
    misDatos() {
      return (
        this.nombre + " " + this.apellidos + "<br>" + "<strong>Sitio web:</strong> " + this.web
      );
    },
  },
  data() {
    return {
      nombre: "Christian Rene",
      apellidos: "Cardenas Sanchez",
      web: "ccardenas.com",
      favorita: null,
      peliculas: [
        {
          title: "Batman vs Superman",
          year: 2017,
          image:
            "https://i0.wp.com/hipertextual.com/wp-content/uploads/2016/03/batman-v-superman-8-scaled.jpg?fit=2560%2C1285&ssl=1",
        },
        {
          title: "Gran Torino",
          year: 2015,
          image:
            "https://cdna.artstation.com/p/assets/images/images/006/306/628/large/armando-romero-gtz-gran-torino-poster.jpg?1497559629",
        },
        {
          title: "Senor de los Anillos",
          year: 2003,
          image:
            "https://www.cinemascomics.com/wp-content/uploads/2021/08/ciudad-serie-el-senor-de-los-anillos-960x720.jpg?mrf-size=m",
        },
        {
          title: "Spiderman",
          year: 2010,
          image:
            "https://es.web.img2.acsta.net/pictures/21/12/01/12/07/0243323.jpg",
        },
      ],
    };
  },
};
</script>