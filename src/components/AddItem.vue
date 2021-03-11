<template>
  <input type="text" placeholder="Add an item" @add-item="addNewItem"><br>
</template>

<script>
export default {
  name: 'AddItem',

  methods: {
    addNewItem() {
      this.todos.push(this.add_todo)
    }
  }
}
</script>

<style>

</style>