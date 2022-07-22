<template>
  <div class="Todo">
    <div class="d-flex justify-content-between align-items-center border rounded p-3" v-if="editMod == false">
      <div>
          {{todoUser.text}}
      </div>
        <div>
              <button class="btn btn-info btn-sm" @click="editTodo">edit</button>
              <button class="btn btn-danger btn-sm ml-1" @click="$emit('deleteTodo', todoUser.key)">delete</button>
        </div>
    </div>




    <div class="d-flex justify-content-between align-items-center border rounded p-3" v-else>
      <div>
          <input type="text" class="form-control" v-model="editedText">
      </div>
        <div>
              <button class="btn btn-info btn-sm" @click="todoEdit">edit</button>
        </div>
    </div>


  </div>
</template>

<script>
export default {
  name: 'Todo',
  emits:[
    'deleteTodo','sendEditedTodo'
  ],
  props: {
      todoUser: Object
  },
  data() {
    return {
      editMod : false ,
      editedText : ''
    }
  },
  methods: {
    editTodo(){
      this.editMod = true
      this.editedText = this.todoUser.text
    },
    todoEdit(){
      this.editMod = false
      this.$emit('sendEditedTodo', { key : this.todoUser.key , text : this.editedText})
      this.editedText = ''
    }
  }

}
</script>
