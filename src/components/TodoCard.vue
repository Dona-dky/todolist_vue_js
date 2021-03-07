<template>
  <div id="fond_blanc">
    <ul id="head">
      <li id="date">{{ date }}</li>
      <li id="titre">{{ letitre }}</li>
      <li id="taches">{{ tasks.length }}{{compteur}}</li>
    </ul>
    
    <new-todo v-on:newTask="submitTask"></new-todo>

    <todo-list
        v-for="(task, index) in tasks"
        :key="index"
        :description="task.description"
        :checked="task.checked"
        v-on:checkTask="checkTask(task)"
        v-on:deleteTask="deleteTask(task)"
        v-on:deleteAllTasks="deleteAllTasks(task)"
        v-on:deleteAllTasksFinished="deleteAllTasksFinished(task)"></todo-list>
        
  </div>
</template>
<script>

import NewTodo from "./NewTodo.vue";
import TodoList from "./TodoList.vue";
export default {
  name: "app",
  components: {
    NewTodo,
    TodoList,
  },

  props: {
    listName: String,
  },

  data() {
    return {
      date: new Intl.DateTimeFormat("fr-FR", { dateStyle: "full" }).format(),
      letitre: "VueJs Tutorial Todo List",
      tasks: [{ description: "Do the dishes", completed: false }],
    };
  },

  methods: {
    //ajouter une tâche
    submitTask(task) {
      this.tasks.push({
        description: task,
        checked: false,
      });
    },

    //   nbrTask() {
    //   if (this.task.length > 1) {
    //     compteur: "tâches",
    //   }else{
    //     compteur: "tâche",
    //   }
      
    // },

    //cocher une tâche
    checkTask(task) {
    task.checked = !task.checked;
    },

    //supprimer une tâche
    deleteTask(deletedTask) {
      this.tasks = this.tasks.filter(task => task !== deletedTask);
    },

        //supprimer une tâche
    // deleteAllTasks() {
    //   // this.tasks = this.tasks();
    //   this.$delete(this.tasks)
    // // this.$store.state.tasks = [];
    // // all.tasks = all.tasks();
    // },
    //supprimer toutes mes tâches
    deleteAllTasks() {
      // this.$buefy.dialog.confirm({
      //   title: `Supprimer toutes mes tâches`,
      //   confirmText: "Supprimer toutes mes tâches",
      //   type: "is-danger",
      //   hasIcon: true,
      //   message: `Etes-vous sûr de vouloir supprimer toutes vos tâches ? Ceci est irréversible.`,
      //   onConfirm: () => {
      //     this.tasks = [];
      //   }
      // });
       this.tasks.$remove();
    },

        //supprimer toutes mes tâches terminées
    deleteAllTasksFinished() {
      // this.$buefy.dialog.confirm({
      //   title: `Supprimer toutes mes tâches`,
      //   confirmText: "Supprimer toutes mes tâches",
      //   type: "is-danger",
      //   hasIcon: true,
      //   message: `Etes-vous sûr de vouloir supprimer toutes vos tâches ? Ceci est irréversible.`,
      //   onConfirm: () => {
      //     this.tasks = [];
      //   }
      // });
       this.tasks.$remove();
    },
  
    

  },
  
};
// console.log($description)
</script>

<style scoped>
#fond_blanc {
  background-color: white;
  border-radius: 10px;
  min-height: 370px;
  width: 600px;
  margin-left: auto;
  margin-right: auto;
}

#head {
  display: flex;
  justify-content: space-between;
  text-align: center;
  padding: 10px 15px;
  background-color: white;
  border-radius: 10px 10px 0 0;
  box-shadow: 0 4px 10px -2px rgba(119, 119, 119, 0.35);
}

#head li {
  color: rgb(114, 112, 112);
  font-weight: bold;
}

#head li:nth-child(2) {
  color: rgb(59, 236, 148);
}
 #task{
   font-size: 25px;
   color: cornflowerblue;
 }
#head li::first-letter {
  text-transform: uppercase;
}
</style>