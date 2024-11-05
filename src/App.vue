<template>
  <h1>My todo list</h1>
  <Form @add="saveTask" />
  <TasksList :tasks="tasks" />
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

    const saveTask = function (data) {
      console.log("App | saveTask() | data", data);
      tasks.value = [...tasks.value, { task: data, id: Date.now() }];
      console.log("App | saveTask() | tasks.value", tasks.value);
    };
    return {
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
  margin-bottom: 20px;
}


</style>
