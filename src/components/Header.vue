<template>
  <div>
    <h1>{{ title }}</h1>
    <Button @toggle-add-task="$emit('toggle-add-task')" :text="showAddTask ? 'close' : 'add task' " :color="showAddTask ? 'btn-info' : 'btn-success'" />
    <Button text="Update task" color="btn-primary" />
    <Button text="Remove task" color="btn-danger" />
  </div>
</template>

<script>
import Button from "./Button";
export default {
  name: "Header",
  props: {
    title: String,
    showAddTask: Boolean
  },
  components: {
    Button,
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
header {
  display: flex;
  justify-content: space-between;
}
</style>
