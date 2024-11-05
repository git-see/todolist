<template>
  <form @submit.prevent="addTask">
    <label for="tache">Add a task</label>
    <input type="text" name="tache" v-model="newTask" />
    <button type="submit" @click="addTask">Add</button>
  </form>
</template>

<script>
import { ref } from "vue";
export default {
  setup(props, ctx) {
    let newTask = ref("");

    const addTask = function () {
      console.log("Form | addTask() | newTask.value", newTask.value);
      ctx.emit("add", newTask.value)
      newTask.value = "";
    };
    return {
      newTask,
      addTask,
    };
  },
};
</script>

<style></style>
