<template>
  <form @submit.prevent="addTask()" id="form">
    <input
      v-model="task"
      autocomplete="off"
      placeholder="Nouvelle tâche..."
      type="text"
    />
    <button v-on:click="addTask" id="add">+</button>

    
  </form>

  <div class="btn_sup">
    <button v-on:click="$emit('deleteAllTasks')" class="delAll">Supprimer toutes mes tâches</button>
    <button v-on:click="$emit('deleteAllTasksFinished')" class="delAll">Supprimer toutes mes tâches terminées</button>
  </div>

  <div id="app"></div>
  <todo-list></todo-list>
</template>

<script>
import TodoList from "./TodoList.vue";
export default {
  name: "app",
  components: {
    TodoList,
  },
  data() {
    return {
      task: ""
    };
  },

  methods: {
    // addTask() {
    //   if (this.newItem.length > 0) {
    //     this.items.push(this.newItem);
    //
    // }this.newItem='';
    // }

    addTask() {
      if (this.task.length > 0) {
        // this.$emit("on-new-todo", this.task);
        this.$emit("newTask", this.task);
      }
      this.task = "";
      
    },
  },
};
</script>

<style scoped>
form {
  margin: 10px auto;
  padding: 5px 0;
  width: 210px;
  display: flex;
  justify-content: space-between;
}

input {
  border: none;
  border-bottom: 2px solid rgb(59, 236, 148);
  height: 40px;
}

input::placeholder {
  color: rgb(201, 197, 197);
  text-align: center;
}

button {
  background-color: rgb(83, 212, 148);
  height: 40px;
  width: 40px;
  border-radius: 50%;
  display: inline-block;
  color: white;
  font-size: 15px;
  font-weight: bold;
  text-align: center;
  align-content: center;
  border: none;
}

.delAll{
  background-color: rgb(165, 29, 24);
  height: 30px;
  width: auto;
  border-radius: 8px;
  margin: 20px 0 10px;
}

.delAll:nth-child(2){
  margin: 0 0 30px;
}

.delAll:hover{
  background-color: rgb(209, 74, 69);
}

.btn_sup{
  /* display: flex; */
  width: 500px;
  margin: 0 auto;
  flex-flow: column;
}
</style>