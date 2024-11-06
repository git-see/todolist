<template>
  <h1>My To Do List</h1>
  <Form @add="saveTask" />
  <TasksList :tasks="tasks" @delete-task="deleteTask" @edit-task="editTask" />
</template>

<script>
import Form from "@/components/Form";
import TasksList from "@/components/TasksList";
import { ref } from "vue";
export default {
  name: "App",
  components: {
    Form,
    TasksList,
  },
  setup() {
    let tasks = ref([]);

    const deleteTask = function (taskName) {
      console.log("App | deleteTask() | taskName", taskName);
      tasks.value = tasks.value.filter((t) => t.id !== taskName.id);
    };

    const editTask = function (taskName) {
      tasks.value = tasks.value.map((t) =>
        t.id !== taskName.id ? t : taskName
      );
    };

    const saveTask = function (data) {
      console.log("App | saveTask() | data", data);
      tasks.value = [...tasks.value, { task: data, id: Date.now() }];
      console.log("App | saveTask() | tasks.value", tasks.value);
    };

    return {
      deleteTask,
      editTask,
      saveTask,
      tasks,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1 {
  font-size: 40px;
  margin-bottom: 60px;
}
</style>
