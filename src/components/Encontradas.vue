<template>
  <div class="container pa-5 my-5 text-center">
    <div class="row">
      <div
        class="col-3"
        v-for="pelicula in peliculasEncontradas"
        :key="pelicula.imdbID"
      >
        <b-card
          :title="pelicula.Title"
          :img-src="pelicula.Poster"
          img-alt="Image"
          img-top
          tag="article"
          style="max-width: 20rem"
          class="mb-2"
        >
          <b-card-text>
            {{ pelicula.Year }}
          </b-card-text>
          <b-icon
            icon="heart"
            variant="secondary"
            v-if="!estaEnFavoritos(pelicula)"
            @click="agregarFavoritos(pelicula)"
          ></b-icon>
          <b-icon icon="heart-fill" variant="danger" v-else ></b-icon>
        </b-card>
      </div>
    </div>
  </div>
</template>

<script>
import { mapState, mapMutations } from "vuex";
export default {
  name: "Encontrados",
  computed: {
    ...mapState(["peliculasEncontradas", "peliculasFavoritas"]),
  },
  methods: {
    ...mapMutations(["AGREGAR_FAVORITOS"]),
    agregarFavoritos(pelicula) {
      this.AGREGAR_FAVORITOS(pelicula);
    },
    estaEnFavoritos(id) {
      if (this.peliculasFavoritas.includes(id)) {
        return true;
      } else {
        return false;
      }
    },
  },
};
</script>

<style>
</style>