<template>
  <div class="to-do-item">
    <div>{{ toDoItem.title }}</div>
    <div>{{ toDoItem.description }}</div>
    <div>{{ toDoItem.dueDate }}</div>
  </div>
</template>

<script>
export default {
  name: "ToDo",
  props: {
    toDoItem: Object,
  },
};
</script>

<style>
.to-do-item {
  display: flex;
  flex-direction: row;
}
</style>