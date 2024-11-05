<template>
  <h3>All my tasks to do</h3>
  {{ tasks.length }} task{{ tasks.length > 1 ? "s" : "" }}
  <ul>
    <li v-for="taskName in tasks" :key="taskName.id">{{ taskName.task }}</li>
  </ul>
</template>

<script>
export default {
  props: {
    tasks: {
      type: Array,
      required: true,
    },
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
  margin: 0;
  width: 100%;
  max-width: 1200px;
  margin: 0 auto;
  margin-top: 20px;
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
