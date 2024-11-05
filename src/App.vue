<template>
  <h1>My todo list</h1>
  <Form @add="saveTask" />
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
</style>
