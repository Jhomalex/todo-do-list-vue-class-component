<template>
  <v-app>
    <TodoList />
  </v-app>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import TodoList from "./components/TodoList.vue";

@Component({
  components: {
    TodoList,
  },
})
export default class App extends Vue {}
</script>

