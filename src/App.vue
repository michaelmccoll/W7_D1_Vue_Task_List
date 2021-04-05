<template>
  <div id="app">
    <h2>To Do List</h2>
    <ul>
      <li v-for='task, index in tasks' v-bind:key="index">
        <span v-if="task.priority==='high'" class='high' >{{task.name}} - {{task.priority}}</span>
        <span v-else class='low'>{{task.name}} - {{task.priority}}</span>
      </li>

    </ul>
    <form v-on:submit.prevent="saveNewTask">
      <label for="new-task"></label>
      <input type="text" id="new-task" v-model="newTask">

      <label class="priority" for="priority" ></label>
      <input name="priority" type="radio" id="high" value="high" v-model="priority">
      <label for="high">High</label>
      <input name="priority" type="radio" id="low" value="low" v-model="priority">
      <label for="low">Low</label>
    

      <input type="submit" value="Save Item">
    </form>

  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return {
      tasks: [
        {name: "Buy Shopping", priority: "low"},
        {name: "Feed Dog", priority: "high"}
        ],
      newTask:""
    }

  },
  methods:{
    saveNewTask: function(){
      this.tasks.push(
        {name: this.newTask, priority: this.priority})
      this.newTask="";
    }

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.high {
  color: red;
  border-color: red;
  border: solid;
  padding: 4px;
  padding-right: 30%;
  padding-left: 30%;
  margin: 4px;
}

.low {
  color: green;
  border-color: green;
  border: solid;
  padding: 4px;
  padding-right: 30%;
  padding-left: 30%;
  margin: 4px;
}

li {
  margin:25px;

  
}

ul{
  list-style-type: none ;
  padding-left: 0px;
}

</style>
