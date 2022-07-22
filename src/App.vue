<template>
  <div class="App">
        <Header/>
        <Welcome @addTodoToList='addToTodos'/>
        <div class="container">
          <TodoList :todos='todos' @deletTodo="deleteTodoFromTodolist" @sendEditedTodo='editTodoList'/>
        </div>
  </div>
</template>

<script>
import Header from '@/components/Header.vue'
import Welcome from '@/components/Welcome.vue'
import TodoList from '@/components/TodoList.vue'

export default {
    name: 'App',
    components: {
      Header,Welcome,TodoList
    },
    data() {
      return {

        todos: [

        {
          key : 1,
          done: true,
          text: 'do your homework'
        },
        {
          key : 2,
          done: true,
          text: 'go to gym'
        },
        {
          key : 3,
          done: true,
          text: 'read a book'
        }


        ]

      }
    },
    methods: {
      addToTodos(val){
        let newTodo = {
          key: this.todos.length + 1,
          done: true,
          text: val
        }
        this.todos.push(newTodo)
      },

      deleteTodoFromTodolist(val){
        let newTodos = this.todos.filter( todo => todo.key != val)
        this.todos = newTodos

      },
      editTodoList({key , text}){
        this.todos = this.todos.map(todo => {
          if (todo.key == key){
            return {
              ...todo,
              text : text
            }

          }else return todo
        })

      }

    }
}
</script>
