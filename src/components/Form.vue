<template>
  <form @submit.prevent="addTask">
    <label for="tache">Add a task</label>
    <input type="text" name="tache" v-model="newTask" />
    <button type="submit">Add</button>
  </form>
</template>

<script>
import { ref } from "vue";
export default {
  setup(props, ctx) {
    let newTask = ref("");

    const addTask = function () {
      console.log("Form | addTask() | newTask.value", newTask.value);
      ctx.emit("add", newTask.value);
      newTask.value = "";
    };
    return {
      newTask,
      addTask,
    };
  },
};
</script>

<style>
form {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1rem;
  border: 1px solid #ccc;
  border-radius: 5px;
  width: 800px;
  max-width: 100%;
  margin: auto;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  background-color: #f9f9f9;
  transition: all 0.3s ease-in-out;
}

form:hover {
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  background-color: #e9e9e9;
}

label {
  font-size: 1.5rem;
  margin-bottom: 1rem;
}

input {
  width: 50%;
  padding: 0.5rem;
  margin-bottom: 1rem;
  border: 1px solid #ccc;
  border-radius: 5px;
}

button {
  width: 150px;
  padding: 0.5rem 1rem;
  background-color: #007bff;
  font-weight: bold;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: all 0.3s ease-in-out;
}

button:hover {
  background-color: #0056b3;
}
</style>
