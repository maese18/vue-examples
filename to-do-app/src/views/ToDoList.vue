<template>
  <div>
    <edit-to-do v-model="editedTodo" @addToDo="addToDo"></edit-to-do>

    <div v-for="item in todoItems" :key="item.id">{{ item.title }}</div>

    <div>
      <pre><code>{{JSON.stringify(todoItems,null,2)}}</code></pre>
    </div>
    <!-- <div>
      <pre><code>{{editedTodo}}</code></pre>
    </div> -->
  </div>
</template>

<script>
import EditToDo from "@/components/EditToDo";
export default {
  name: "ToDoList",
  components: {
    EditToDo,
  },

  data() {
    return {
      editedTodo: { title: "", description: "", dueDate: "" },
      todoItems: [
        {
          id: 0,
          title: "Mein erstes ToDo",
          description: "Detaillierte Beschreibung der Aufgabe",
          dueDate: "2022-04-30",
          completed: false,
        },
        {
          id: 1,
          title: "Auto waschen",
          description: "in Waschanlage fahren...",
          dueDate: "2022-04-21",
          completed: false,
        },
      ],
    };
  },
  computed: {
    incompleteCount() {
      return 0; // TODO: Calculate incomplete count
    },
  },
  methods: {
    addToDo() {
      this.todoItems.push({
        id: this.todoItems.length + 1,
        ...this.editedTodo,
      });
      this.editedTodo = { title: "new", description: "", dueDate: "" };
    },
  },
};
</script>

<style>
</style>