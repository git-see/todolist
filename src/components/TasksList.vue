<template>
  <h3>All my tasks to do</h3>
  {{ tasks.length }} task{{ tasks.length > 1 ? "s" : "" }}
  <ul>
    <li v-for="taskName in tasks" :key="taskName.id">
      <div id="buttonsContainer">
        <button @click="deleteTask(taskName)" id="deleteButton">X</button>
        <button @click="editTask(taskName)" id="editButton">&#x2B6F;</button>
      </div>
      <span v-if="taskToEdit !== null && taskToEdit.id === taskName.id">
        <input
          type="text"
          v-model="taskToEdit.task"
          @keypress.enter="saveTask"
        />
        <button @click="saveTask">Save</button>
      </span>
      <span v-else>{{ taskName.task }}</span>
    </li>
  </ul>
</template>

<script>
import { ref } from "vue";
export default {
  emits: ["delete-task", "edit-task"],
  props: {
    tasks: {
      type: Array,
      required: true,
    },
  },
  setup(props, { emit }) {
    let taskToEdit = ref(null);

    let deleteTask = function (taskName) {
      emit("delete-task", taskName);
    };

    let editTask = function (taskName) {
      taskToEdit.value = taskName;
    };

    let saveTask = function () {
      emit("edit-task", taskToEdit.value);
      taskToEdit.value = null;
    };
    return {
      deleteTask,
      editTask,
      saveTask,
      taskToEdit,
    };
  },
};
</script>

<style>
h3 {
  font-size: 25px;
  margin-top: 65px;
  margin-bottom: 20px;
}

ul {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding: 0;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  margin-top: 20px;
  margin-bottom:80px;
}

li {
  width: 20%;
  margin: 10px;
  padding: 30px;
  border: 1px solid #2c3e50;
  border-radius: 5px;
  background-color: #2c3e50;
  color: #fff;
  font-size: 20px;
  text-align: center;
  cursor: pointer;
  word-wrap: break-word;
  overflow-wrap: break-word;
}

#buttonsContainer {
  display: flex;
  justify-content: space-between;
  align-items: center;
}

#deleteButton,
#editButton {
  padding: 0.5em;
  width: 30px;
  margin-bottom: 20px;
  border: none;
  border-radius: 5px;
  font-size: 15px;
  transition: background-color 0.3s ease-in-out;
}

#deleteButton {
  background-color: orangered;
}

#editButton {
  background-color: #45b342;
}

#deleteButton:hover {
  background-color: red;
}

#editButton:hover {
  background-color: #0e6b0a;
}
</style>
