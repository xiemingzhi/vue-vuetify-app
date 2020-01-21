<template>
  
  <v-card>
    <v-list>
      <v-list-item v-for="todo in todos" :key="todo.id">
        <v-list-item-content>
          <v-list-item-title>{{todo.title}}</v-list-item-title>
        </v-list-item-content>
      </v-list-item>
    </v-list>
    <v-btn
      absolute
      dark
      fab
      bottom
      right
      color="pink"
      @click="addTodo"
    >
      <v-icon>mdi-plus</v-icon>
    </v-btn>
  </v-card>
</template>

<script>
import axios from 'axios';

export default {
  data() {
    return {
      todos: []
    }
  },
  methods: {
    addTodo() {
      this.$router.push({path: '/todos/add'})
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=10')
      .then(res => this.todos = res.data)
  },
  mounted () {
    // eslint-disable-next-line no-console
    console.log('todos length', this.todos.length)
  },
}</script>

<style lang="scss" scoped>
.todo-fab {
  position: fixed;
  bottom: 25px;
  right: 15px;
  font-size: 30px;
}

.content {
  padding: 10px 10px 10px 0px
}
</style>
