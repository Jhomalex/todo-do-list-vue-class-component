<template>
  <div style="width: 100%">
    <v-row align="center">
      <v-icon color="#6e6bff" v-if="finished">check_circle</v-icon>
      <v-icon v-else>remove_circle</v-icon>
      <span v-text="name" />
    </v-row>
    <v-row>
      <v-divider></v-divider>
    </v-row>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from "vue-property-decorator";

@Component
export default class Item extends Vue {
  @Prop() name!: string;
  @Prop() finished!: boolean;
}
</script>

<style scoped>
</style>