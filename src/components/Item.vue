<template>
  <div>
    <li>
      <label>
        <input
          type="checkbox"
          :checked="todo.done"
          @click="handleCheck(todo.id)"
        />
        <span>{{ todo.title }}</span>
      </label>
      <button class="btn btn-danger" @click="handledelete(todo.id)">
        删除
      </button>
    </li>
  </div>
</template>

<script>
export default {
  name: "Item",
  props: ["todo", "checkTodo", "deleteTodo"],
  methods: {
    handleCheck(idd) {
      this.checkTodo(idd);
    },
    handledelete(id) {
      if (confirm("确定删除吗")) {
        this.deleteTodo(id);
      }
    },
  },
};
</script>

<style scoped>
/*item*/
li {
  list-style: none;
  height: 36px;
  line-height: 36px;
  padding: 0 5px;
  border-bottom: 1px solid #ddd;
}

li label {
  float: left;
  cursor: pointer;
}

li label li input {
  vertical-align: middle;
  margin-right: 6px;
  position: relative;
  top: -1px;
}

li button {
  float: right;
  display: none;
  margin-top: 3px;
}

li:before {
  content: initial;
}

li:last-child {
  border-bottom: none;
}
li:hover {
  background-color: rgb(146, 156, 156);
}
li:hover button {
  display: block;
}
</style>