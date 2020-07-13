<template>
  <div>
    <form @submit.prevent="addTodo">
      <input type="text" v-model="title" placeholder="Opret ny opgave..." />
      <input type="submit" value="Opret" class="btn" />
    </form>
  </div>
</template>

<script>
import { v4 as uuidv4 } from "uuid";
export default {
  name: "addTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo() {
      if (this.title !== "") {
        const newTodo = {
          id: uuidv4(),
          title: this.title,
          completed: false
        };
        this.title = "";
        //send til parent
        this.$emit("add-todo", newTodo);
        //console.log(this.title),
      }
    }
  }
};
</script>

<style scoped>
form {
  display: flex;
}
input[type="text"] {
  flex: 10;
  padding: 10px;
}

input[type="submit"] {
  flex: 2;
}
</style>