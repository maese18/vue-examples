<template>
  <div>
    <form @submit="$emit('addToDo')">
      <input type="text" v-model="title" name="title" />
      <input type="text" v-model="description" name="Beschreibung" />
      <input type="date" v-model="dueDate" name="Fällig" />

      <button type="submit">Hinzufügen</button>
    </form>
  </div>
</template>

<script>
export default {
  name: "EditToDo",
  props: {
    value: Object,
  },
  data() {
    return {
      title: this.value ? this.value.title : "",
      description: this.value ? this.value.description : "",
      dueDate: this.value ? this.value.dueDate : "",
    };
  },
  methods: {
    initFromValue(value) {
      this.title = value ? value.title : "";
      this.description = value ? value.description : "";
      this.dueDate = value ? value.dueDate : "";
    },
    /**
     * Sends the to do object to the parent component
     * The property 'value' combined with this.$emit('input', VALUE) forms the v-model for this component
     */
    emitModel() {
      this.$emit("input", {
        title: this.title,
        description: this.description,
        dueDate: this.dueDate,
      });
    },
  },
  watch: {
    title() {
      this.emitModel();
    },
    description() {
      this.emitModel();
    },
    dueDate() {
      this.emitModel();
    },
    value(newValue) {
      this.initFromValue(newValue);
    },
  },
};
</script>

<style>
</style>