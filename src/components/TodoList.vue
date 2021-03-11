<template>
  <div class="todo-list">
    <TodoItem
      v-for="todo in todos"
      :key="todo.id"
      :todoProps="todo"
      @item-completed="markCompleted"
      @delete-item="deleteTodo"
    />
  </div>
  <div class="add-item">
    <input
      class="add-item-btn"
      v-if="!isAddTodo"
      type="submit"
      value="Add an item"
      @click="handleAdd"
    />
    <textarea
      rows="3"
      cols="70"
      v-else
      type="text"
      placeholder="Add an item"
      v-model="inputValue"
    />
  </div>
  <button class="add-btn" @click="addItem" v-show="isAddTodo">Add</button>
</template>

<script>
import { ref } from "vue";
import TodoItem from "./TodoItem";
import { uid } from "uid";

export default {
  name: "TodoList",
  components: { TodoItem },
  setup() {
    const todos = ref([]);
    const isAddTodo = ref(false);
    const inputValue = ref("");
    const handleAdd = () => {
      // update status isAddTodo
      isAddTodo.value = !isAddTodo.value;
    };
    const markCompleted = (id) => {
      todos.value = todos.value.map((todo) => {
        if (todo.id === id) todo.completed = !todo.completed;
        return todo;
      });
    };

    const deleteTodo = (id) => {
      todos.value = todos.value.filter((todo) => todo.id != id);
    };

    const addItem = () => {
      todos.value.push({
        id: uid(),
        title: inputValue.value,
        completed: false,
      });
      console.log(inputValue.value);
      inputValue.value = "";
    };

    return {
      todos,
      markCompleted,
      deleteTodo,
      addItem,
      isAddTodo,
      handleAdd,
      inputValue,
    };
  },
};
</script>

<style>
textarea {
  background-color: #fff;
  box-shadow: inset 0 0 0 2px #0079bf;
  cursor: text;
  resize: vertical;
  float: none;
  border-radius: 3px;
  overflow: hidden;
  overflow-wrap: break-word;
  padding: 8px 12px;
  margin: 0 15px;
  outline: none;
  border: none;
}
.add-item {
  margin: 10px 33px;
}
.add-btn {
  border: none;
  padding: 5px 10px;
  margin: 5px 33px;
  background: rgb(71, 148, 71);
  color: #fff;
  border-radius: 3px;
  cursor: pointer;
  margin: 0 50px;
}
.add-btn:hover {
  background: rgb(93, 173, 93);
}
.task,
.input-task {
  float: left;
}
.add-item-btn {
  border: none;
  background: #ebecf0;
  border-radius: 3px;
  padding: 5px 15px;
  margin: 0 10px;
}
</style>