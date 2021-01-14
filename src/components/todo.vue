<template>
<div class="container">
  <h2> My tasks</h2>
  <div class="todo-input">
        <input type="text" id="task" v-model="task" name="task" placeholder="enter your task here" class="add-input">
        <button class="add-btn" type="button" v-on:click="addTodo()">+</button>
  </div>
<div class="todo-tasks">
    <!--<div class="todo-task">
      lkhjgfd
      <span class="task-delete"><i class="fa fa-trash" style="font-size:25px;color:#4471D2"></i> </span>
      <span class="task-check-2"><i class="fa fa-check-circle" style="font-size:25px;color:#1FE9B7"></i> </span>
    </div>-->

    <div class="todo-task" v-for="(todo, index) in todos" :key="index" >
     <div class="todo-text" v-bind:class="{ 'task-done': todo.checked }">{{todo.task}} </div>
      <span class="task-delete" v-on:click="removeTodo(index)"><i class="fa fa-trash" style="font-size:25px;color:#4471D2"></i> </span>
      <span class="task-check" v-bind:class="{ 'show-done': todo.checked }" ><i class="fa fa-check-circle" style="font-size:25px;color:#1FE9B7"></i> </span>
      <span class="task-check" v-bind:class="{ 'add-mark': !todo.checked }" v-on:click="addDone(todo.task)" ><i class="fa fa-circle-o" style="font-size:25px;color:#1FE9B7"></i> </span>
    </div>
</div>
</div>
</template>

<script>
export default {
  name: 'todo',
  arra: ['judd ', 'sss'],
  data: function () {
    const list = [
      {
        'task': 'Morning run',
        'checked': true
      },
      {
        'task': 'Meeting with collegues',
        'checked': false
      },
      {
        'task': 'Renew gym membership',
        'checked': false
      }
    ]

    function removeTodo (index) {
      console.log('rmove a slice', list)
      list.splice(index, 1)
    }
    function addTodo () {
      var obj = {
        'task': this.task,
        'checked': false
      }
      list.push(obj)
      this.task = null
    }
    function addDone (task) {
      console.log('index ', task)
      var found = list.find(x => x.task === task)
      found.checked = true
      // console.log('found ', list.find(x => x.task === task))
    }
    return {
      todos: list,
      removeTodo,
      addTodo,
      addDone,
      task: null
    }
  }
  /* methods: {
    removeTodo (index) {
      console.log('rmove a slice', this.arra)
      //  this.list.value.splice(index, 1)
      this.arra.slice(index, 1)
    }
  } */
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
.container{
  border: 1px solid #dadce0;
  width: 100%;
  display: block;
  margin: auto;
  padding: 10px;
  border-radius: 8px;
  margin-top: 60px;
  max-width: 520px;
}
.todo-input{
  display: inline-block;
}
.add-input{
  padding: 10px;
  border-radius: 5px;
  width: 300px;
  margin-right: 10px;
  border: none;
  outline: none;
  font-size: 1em;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
}
.add-btn{
  border-radius: 50px;
  height: 40px;
  width: 40px;
  background: #518AFF;
  color: #fff;
  font-size: 23px;
  box-shadow: rgba(50, 50, 93, 0.25) 0px 2px 5px -1px, rgba(0, 0, 0, 0.3) 0px 1px 3px -1px;
  outline: none;
  border: none;
  cursor: pointer;
}
.todo-tasks{
  margin-top:20px;
}
.todo-task{
  box-shadow: 0 5px 9px rgba(50,50,93,.1), 0 3px 7px rgba(0,0,0,.04);
  background: #fff;
  border-radius: 35px;
  padding: 15px;
  width: 90%;
  margin: auto;
  color: #3d5079;
  margin-bottom: 15px;
}
.todo-task:hover{
  transform: scale(.95);
  transition: all .3s cubic-bezier(.215,.61,.355,1);
}
.task-delete{
  float: right;
  margin-right: 10px;
  cursor: pointer;
}
.task-check{
  float: right;
  margin-right: 20px;
  cursor: pointer;
  display: none;
}
.add-mark{
  display: block;
}
.task-done{
   text-decoration: line-through;
   color: #949EB4;
}
.show-done{
  display: block;
}
.todo-text{
  display: inline-block;
  width: 70%;
}
@media (max-width: 500px) {
.todo-text{
  text-align: left;
  font-size: 14px;
}
}
</style>
