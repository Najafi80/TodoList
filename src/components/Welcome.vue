<template>
  <div class="Welcom">
      <section class="jumbotron">
        <div class="container d-flex flex-column align-items-center">
            <h1 class="jumbotron-heading">Welcome!</h1>
            <p class="lead text-muted">To get started, add some items to your list:</p>
            <div class="form-inline">
                <div class="form-group">
                    <input type="text" class="form-control mx-sm-3" placeholder="I want to do ..." v-model="item">
                    <button class="btn btn-primary" @click="addTodo">add</button>
                </div>
            </div>
        </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Welcome',
  emits:[
    'addTodoToList'
  ],
  data() {
    return {
      item: ''
    }
  },
  methods: {
    addTodo(){
      this.$emit('addTodoToList', this.item)
      this.item = ''
    }
  },

}
</script>
