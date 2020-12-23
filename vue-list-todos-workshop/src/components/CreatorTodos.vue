import { default } from '../App.vue';
<template>
  <div>      
    <div class="md-layout alineado">
      <div class="md-layout-item md-size-15"></div>
      <div class="md-layout-item md-size-70">
        <md-field>
          <label>Introduce tu tarea!</label>
          <md-input v-model="nameTodo" type="text"></md-input>
          <span class="md-helper-text"></span>
        </md-field>
      </div>
      <div class="md-layout-item md-size-15">
        <md-button @click="addTodo" class="md-icon-button md-raised md-primary">
          <md-icon>add</md-icon>
        </md-button>
      </div>
    </div>

    
      
    
  </div>
  
</template>

<script>
export default {
  name: "CreatorTodos",
  data() {
    return {
      nameTodo: "",
    };
  },
  methods: {
    addTodo() {
      this.$emit("add-todo", this.nameTodo);
    },
  },
};
</script>

<style scoped>

.alineado{
  display: flex;
  justify-content:center;
  align-items: center;
}

</style>
