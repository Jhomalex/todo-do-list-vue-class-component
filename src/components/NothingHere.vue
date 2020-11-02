<template>
  <div>
    <v-row align="center" justify="center">
      <v-col cols="2">
        <v-img
          src="https://i.pinimg.com/originals/66/a6/0e/66a60e67010ee1024d27b5cea4cb32b3.jpg"
          width="150"
        ></v-img>
      </v-col>
      <v-col cols="4">
        <span class="text">Aún no tienes tareas creadas...</span>
      </v-col>
    </v-row>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";

@Component
export default class NothingHere extends Vue {}
</script>

<style scoped>
.text {
  font-size: 24px;
  color: rgb(84, 84, 84);
}
</style>