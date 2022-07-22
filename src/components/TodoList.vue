<template>
    <div class="todoList">
            <div class="d-flex flex-column align-items-center">
                <nav class="col-6 mb-3">
                    <div class="nav nav-tabs" id="nav-tab" role="tablist">
                        <a class="nav-item nav-link active font-weight-bold" id="nav-home-tab">undone <span class="badge badge-secondary">3</span></a>
                        <a class="nav-item nav-link font-weight-bold" id="nav-profile-tab">done <span class="badge badge-success">9</span></a>
                    </div>
                </nav>


              <Todo
              class="col-6 mb-2"
              v-for="todoUser in todos"
              :key="todoUser.key"
              :todoUser='todoUser'
              @deleteTodo="$emit('deletTodo', $event)"
              @sendEditedTodo="$emit('sendEditedTodo', $event )"
              />



                  </div>

            </div>


</template>

<script>
import Todo from "@/components/Todo.vue"
export default {
  name: 'TodoList',
  emits:[
    'deletTodo', 'sendEditedTodo'
  ],
  components: {
    Todo
  },
  props:{
    todos: Array
  }

}
</script>
