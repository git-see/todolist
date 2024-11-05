<template>
  <h1>My todo list</h1>
  <Form @add="saveTask" />
  <ul>
    <li v-for="taskName in tasks" :key="taskName.id">{{ taskName.task }}</li>
  </ul>
  {{ tasks.length }} task{{ tasks.length > 1 ? "s" : "" }}
</template>

<script>
import Form from "@/components/Form";
import { ref } from "vue";
export default {
  name: "App",
  components: {
    Form,
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

ul {
  list-style: none;
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  padding: 0;
  margin: 0;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  margin-top: 20px;
}

h1 {
  font-size: 40px;
  margin-bottom: 20px;
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
</style>
