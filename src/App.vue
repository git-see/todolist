<template>
  <h1>My todo list</h1>
  <Form @add="saveTask" />
</template>

<script>
import Form from "@/components/Form";
export default {
  name: "App",
  components: {
    Form,
  },
  setup() {
    const saveTask = function (data) {
      console.log("App | saveTask() | data", data);
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
