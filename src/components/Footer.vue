<template>
  <div class="todo-footer">
    <label>
      <input type="checkbox" @change="checkAll" :checked="isAll" />
    </label>
    <span>
      <span>已完成{{ doneTotal }}</span> / 全部{{ todos.length }}
    </span>
    <button class="btn btn-danger" @click="clearAll">清除已完成任务</button>
  </div>
</template>

<script>
export default {
  name: "Footer",
  props: ["todos", "checkAllTodo", "deleteTodo"],
  computed: {
    doneTotal() {
      // reduce专门用来做条件统计 第一个参数函数,函数可以传两个值 pre cur
      return this.todos.reduce((pre, cur) => pre + (cur.done ? 1 : 0), 0);
      //return this.todos.filter((todo) => todo.done).length;
    },
    isAll() {
      return this.doneTotal == this.todos.length;
    },
  },
  methods: {
    checkAll(e) {
      this.checkAllTodo(e.target.checked);
      console.log(e.target);
    },
    clearAll() {
      for (let item of this.todos) {
        if (item.done) {
          console.log(item);
          this.deleteTodo(item.id);
        }
      }
    },
  },
};
</script>

<style scoped>
/*footer*/
.todo-footer {
  height: 40px;
  line-height: 40px;
  padding-left: 6px;
  margin-top: 5px;
}

.todo-footer label {
  display: inline-block;
  margin-right: 20px;
  cursor: pointer;
}

.todo-footer label input {
  position: relative;
  top: -1px;
  vertical-align: middle;
  margin-right: 5px;
}

.todo-footer button {
  float: right;
  margin-top: 5px;
}
</style>