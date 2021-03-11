<template>
  <li
    :class="['todo-item', todoProps.completed ? 'is-completed' : '']"
  >
    <input
      class="checkbox"
      type="checkbox"
      :checked="todoProps.completed"
      @change="markItemCompleted"
    />
    <span class="title">
      {{ todoProps.title }}
    </span>
    <button class="del-btn" @click="deleteItem">Delete</button>
  </li>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todoProps"],
  setup(props, context) {
    const isDeleted = false;
    const markItemCompleted = () => {
      context.emit("item-completed", props.todoProps.id);
    };
    const deleteItem = () => {
      context.emit("delete-item", props.todoProps.id);
    };

    return {
      markItemCompleted,
      deleteItem,
      isDeleted,
    };
  },
};
</script>

<style>
span {
  margin: 0 10px;
}
.todo-item {
  list-style: none;
  padding: 5px 10px;
  transition-duration: 0.14s;
  transition-timing-function: ease-in;
}
.todo-item:hover {
  background: #ebecf0;
}
.del-btn {
  background: rgb(201, 201, 201);
  border: none;
  float: right;
  display: none;
  color: rgb(59, 59, 59);
  border-radius: 3px;
}
.todo-item:hover > .del-btn {
  display: block;
}
.is-completed {
  text-decoration: line-through;
}
.checkbox {
  border-radius: 2px;
  height: 16px;
  width: 16px;
  overflow: hidden;
  white-space: nowrap;
  transition: all 0.2s ease-in-out;
  background-color: #fafbfc;
  box-shadow: inset 0 0 0 2px #dfe1e6;
  top: 5px;
  border: none;
  text-align: center;
  cursor: pointer;
  padding: 0;
  margin: 0;
}
.checkbox:hover {
  background: #ebecf0;
  box-shadow: inset 0 0 0 2px #dfe1e6;
}
.title {
  margin: 0 24px;
  width: 100px;
  overflow: hidden;
}
</style>