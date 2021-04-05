<template>
  <div class="favoritos">
  <table class="table">
  <thead>
    <tr>
      <th scope="col">Película</th>
    </tr>
  </thead>
  <tbody>
    <tr v-for="(item, index) in peliculasFavoritas" :key="index">
      <td>{{item.Title}}</td>


    </tr>
  </tbody>
</table>
  </div>
</template>

<script>
import {mapState} from "vuex"

export default {
  name:"favoritos",
  computed: {
    ...mapState(["peliculasFavoritas"])
  }
}
</script>
