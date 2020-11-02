<template>
  <v-container style="padding-top: 50px">
    <v-row>
      <h1 style="color: #6e6bff; font-size: 22px">TASKS</h1>
      <v-btn
        small
        color="#6e6bff"
        dark
        style="margin-left: 15px"
        @click="cleanTasks()"
        ><v-icon>cleaning_services</v-icon>Clean</v-btn
      >
    </v-row>
    <v-row>
      <v-text-field
        placeholder="Add task"
        prepend-inner-icon="add"
        color="#6e6bff"
        v-model="newTask"
        @keyup.enter="addTask()"
      />
    </v-row>
    <div v-if="countAllTasks > 0">
      <v-row>
        <v-col cols="12" v-for="task in pendingTasks" :key="task.id">
          <Item
            :name="task.name"
            :finished="false"
            v-on:dblclick.native="finishTask(task)"
          />
        </v-col>
      </v-row>
      <v-row style="margin-top: 30px" v-show="completedTasks.length > 0">
        <p style="font-size: 20px; font-weight: 600; margin: 0px">Completed</p>
        <v-col cols="12" v-for="task in completedTasks" :key="task.id">
          <Item
            :name="task.name"
            :finished="true"
            v-on:dblclick.native="returnTask(task)"
          />
        </v-col>
      </v-row>
    </div>
    <div v-else>
      <NothingHere />
    </div>
  </v-container>
</template>

<script lang="ts">
import { Component, Vue } from "vue-property-decorator";
import Item from "@/components/Item.vue";
import NothingHere from "@/components/NothingHere.vue";
import { Task } from "@/interfaces/index";

@Component({ components: { Item, NothingHere } })
export default class TodoList extends Vue {
  newTask = "";
  pendingTasks: Array<Task> = [];
  completedTasks: Array<Task> = [];

  get countAllTasks() {
    return this.pendingTasks.length + this.completedTasks.length;
  }

  addTask() {
    const time = new Date();
    const task: Task = {
      id: time.getTime(),
      name: this.newTask,
    };
    this.pendingTasks.push(task);
    this.newTask = "";
  }

  finishTask(task: Task) {
    this.completedTasks.push(task);
    this.pendingTasks = this.pendingTasks.filter((pending) => {
      if (pending.id != task.id) {
        return pending;
      }
    });
  }

  returnTask(task: Task) {
    this.pendingTasks.push(task);
    this.completedTasks = this.completedTasks.filter((completed) => {
      if (completed.id != task.id) {
        return completed;
      }
    });
  }

  cleanTasks() {
    this.pendingTasks = [] as Array<Task>;
    this.completedTasks = [] as Array<Task>;
  }
}
</script>

<style scoped>
</style>