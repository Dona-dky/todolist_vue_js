<template id="todolist">

    <li class="list is-flex">
    <div class="left">
    <form
      class="btn border-0 flex-grow-1 text-left shadow-none "
      :class="{ checked }"
      @click="$emit('checkTask')"
    >
    <i class="far fa-circle"></i>
      <span>{{ description }}</span>
    </form>
    </div>

    <div class="right">
    <button v-on:click="$emit('deleteTask')">
      <i class="fas fa-trash"></i>
    </button>
            <div class="TodoItem__reorderHandle">
      <i class="fa fa-bars" />
    </div>
    </div>

  </li>
  
</template>

 <script>
export default {
  // name: "app",

  // data() {
  //   return {
  //     newTodo: "",
  //   };
  // },

    props: {
      description: String,
      checked: Boolean
  },
  
};
</script>

<style scoped>

.checked{
  text-decoration:line-through;
}

.left{
  padding-top: 6px;
}
.right button{
  margin-right: 10px;
}
/* .list{
  display: none;
} */
li {
  margin: 0 30px;
  justify-content: space-between;
  display: inline-flex;
  padding: 10px 0;
}

li span {
  margin:0 15px;
}

/* .fas,.far{
  background-color: crimson;

} */

button ,.TodoItem__reorderHandle{
  background-color: rgb(165, 29, 24);
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

.TodoItem__reorderHandle{
  background-color: rgb(230, 95, 33);
}

.TodoItem__reorderHandle i{
  padding-top: 13px;
}

</style>