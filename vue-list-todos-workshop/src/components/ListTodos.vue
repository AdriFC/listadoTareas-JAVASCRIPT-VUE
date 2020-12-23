<template>
  <div>
    <ul>
      <li v-for="todo in listTodos" :key="todo.id">
        <div class="md-layout alineado">
          <div class="md-layout-item md-alignment-bottom-center alineado">
            <span :class="{ completed: todo.completed }"> {{ todo.name }} </span>
            <!--<button @click="updateTodo(todo.id)">x</button>-->
            <md-button @click="updateTodo(todo.id)" class="md-icon-button md-mini">
              <md-icon>done</md-icon>
            </md-button>
          </div>
        </div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "ListTodos",
  props: {
    listTodos: {
      type: Array,
      default: () => [],
    },
  },
  methods: {
    updateTodo(idTodo) {
      this.$emit("update-todo", idTodo);
    },
  },
};
</script>

<style scoped>
.completed {
  text-decoration: line-through;
}
ul li {
  list-style: none;
}
.alineado{
  display: flex;
  justify-content:center;
  align-items: center;
}
</style>
