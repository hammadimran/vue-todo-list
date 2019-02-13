<template>
  <el-row :gutter="20">
    <el-col :span="22":offset="12">
      <h1 class="top">TO-DO:</h1>
      <div class="wrapper">
        <div class="controls">
          <input v-model="newTodo"  type="text" placeholder="New tasks go here..." autofocus class="in">
          <el-date-picker
            v-model="newdate"
            type="date"
            placeholder="Pick a date"
            default-value="2018-08-1">
          </el-date-picker>
          <el-button type="success" plain class="add" v-on:click="addTodo">Add</el-button>
          <el-button type="danger" plain class="clear" v-on:click="clearTodos">Clear All</el-button>
        </div>
        <ul>
          <todo-item v-for="(todo, index) in todos" :key="todo.id"
                     v-bind:title="todo.title"
                     v-bind:date="todo.date"
                     v-bind:completed="todo.completed"
                     v-on:toggle="toggle(index)"
                     v-on:delete="deleteTodo(index)"></todo-item>
        </ul>
      </div>
    </el-col>
  </el-row>
</template>
<script>
  import mylist from './todo-item'
  import moment from 'moment';
    export default {
        name: "mycomponent",
      data: function() {
        return {
          newTodo: '',
          newdate: '',
          todos: [{ title: 'Just a todo', completed: true, date:''} ]
        }
      },
      components:{
          'todo-item': mylist,
      },
      methods: {
        addTodo() {
          var date_entered = moment(this.newdate).format("LL");
          console.log(date_entered);
          var todayDate2 = new Date();
          var todayDate1 = moment(todayDate2).format("LL");
          var todayDate3 = moment(todayDate2).add(1, 'day').format("LL");
          console.log(todayDate3);
          if( date_entered === todayDate1){
            this.newdate = 'Today';}
          else if(date_entered === todayDate3 ){
            this.newdate = ' Tommorrow';}
          else{
            var day = moment(this.newdate).format("dddd");
            this.newdate = " on " + date_entered + "  " + day;}
          this.todos.push({ title: this.newTodo, completed: false , date: this.newdate});
          this.newTodo = '';
          this.newdate = '';
        },
        toggle(index) {
          this.todos[index].completed = !this.todos[index].completed;},
        deleteTodo(index) {
          this.todos.splice(index, 1);},
        clearTodos() {
          if (this.todos.length < 1) return;
          if (confirm('Want to clear all todos?')) {
            this.todos = [];
          }
        }
      }
    }


</script>

<style>

  .in{
    -webkit-border-radius:8px;
    margin-right: 10px;
  }
  html,
  body {
    margin: 0;
    padding: 0;
    width: 896px;
    height: 100%;
    background-image: url("../assets/1.jpg");
    color: #006666;
  }

  body {
    font-family: "Segoe UI";
    font-size: 1.5em;
  }

  .wrapper {
    padding: 0 20px;
  }

  .controls {
    display: flex;
    flex-flow: row wrap;
    justify-content: space-around;
  }
  .controls input {
    flex: 8;
  }

  .completed {
    text-decoration: line-through;
    color: gray;
  }

  .top {
    background-color: #BBA3D0;
    width: 100%;
    color:  #993366;
    font-style: italic;
    text-align: center;
    margin-top: 0px;
    -webkit-border-radius:17px;

  }

  input {
    padding: 8px;
    border-radius: 4px 4px 4px 4px;
    background-color: #fff;
    width: 40%;
  }

  ul {
    padding: 0;
  }

  li {
    list-style: none;
    padding: 8px;
    font-size: 1em;
  }

  button {
    color: #fff;
    border: none;
    border-radius: 2px 2px 2px 2px;
    padding: 8px;
    margin-left: 8px;
    text-transform: uppercase;
    font-weight: 800;
  }

  button.add {
    background-color: #009933;
    margin-left: 7px;
  }

  button.add:hover {
    background-color: #007a29;
  }

  button.remove {
    background-color: #dc143c;
  }

  button.remove:hover {
    background-color: #b01030;
  }

  .btn {

    padding: 2px 4px 2px 4px;
    margin-bottom: 10px;
  }




</style>
