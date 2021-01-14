<template>
  <div id="app">
    <h1> My first todo list with Vue.js</h1>
    <todo/>
    <footer class="todo-footer">
          Todo app with Vue.js framework - © Juda Buchahda 2021
          <a href="https://juda-landing-cv.herokuapp.com"> Juda Buchahda </a>
    </footer>
  </div>
</template>

<script>
import todo from './components/todo'

export default {
  name: 'App',
  components: {
    todo
  }
}
</script>

<style>
#app {
  font-family: 'Poppins', sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
    color: #518AFF;
    font-weight: 500;
}
h2{
  color: #3d5079;
}
.todo-footer{
  position: absolute;
    bottom: 0;
    left: 50%;
    transform: translate(-50%,-50%);
    text-align: center;
}
/* Screen larger than 500px */
@media (max-width: 500px) {
  h1{
font-size: 20px;
}
 .todo-footer{
  width: 80%;
  font-size: 12px;
  bottom: 0;
  text-align: center;
}
}
</style>
