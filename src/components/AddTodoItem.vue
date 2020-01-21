<template>
<v-card>
  <v-form>
      <v-text-field
        label="Regular"
        :value="name" ref="newTodoItem" @input="updateTodoName"
      ></v-text-field>
  </v-form>
  <v-btn
      absolute
      dark
      fab
      bottom
      right
      color="pink"
      @click="addTodo"
    >
    <v-icon>mdi-check</v-icon>
  </v-btn>
</v-card>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      name: ''
    }
  },
  methods: {
    addTodo() {
      const newTodo = { name: this.name }
      axios.post('https://jsonplaceholder.typicode.com/todos', newTodo)
        .then(res => {
          // eslint-disable-next-line no-console
          console.log('addtodo', res)
          this.$router.push({path: '/todos'})
        })
    },
    updateTodoName() {
      this.name = this.$refs.newTodoItem.value
    }
  }
}
</script>

<style lang="scss" scoped>
.todo-fab {
  position: fixed;
  bottom: 25px;
  right: 15px;
  font-size: 30px;
}
</style>