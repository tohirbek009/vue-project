<template>
  <div class="container">
    <Header @toggle-add-task='toggleAddTask' title='Track' :showAddTask="showAddTask" />
    <div v-if='showAddTask'>
      <AddTask @add-task="addTask"/> 
    </div>
    <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue'
import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components:{
    Header,
    Tasks,
    AddTask
  },
  data(){
    return{
      tasks: [],
      showAddTask: false
    }
  },
  methods:{
    toggleAddTask(){
      this.showAddTask = !this.showAddTask;
    },
    deleteTask(id){
      if(confirm("Are you sure to delete?")){
        this.tasks = this.tasks.filter((task) => task.id !== id)
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task) => task.id === id ? {...task, remainder: !task.remainder}: task)
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    }
  },
  created(){
    this.tasks = [
      {
        id: 1,
        text: 'Liverpool was created',
        day: '1st March, 1989, at 2:30pm',
        remainder: true
      },
      {
        id: 2,
        text: 'Barselona was created',
        day: '1st January, 1975, at 2:30pm',
        remainder: true
      },
      {
        id: 3,
        text: 'Chelsea was created',
        day: '1st March, 1919, at 2:30pm',
        remainder: false
      },
    ]
  }
}
</script>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Poppins:ital,wght@0,600;0,700;1,400;1,500&display=swap');
  *{
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  body {
    font-family: "Poppins", sans-serif;
  }

  .container {
    max-width: 500px;
    margin: 30px auto;
    overflow: auto;
    min-height: 300px;
    border: 1px solid steelblue;
    padding: 30px;
    border-radius: 5px;
  }
  .btn {
    display: inline-block;
    background: #000;
    color: #fff;
    border: none;
    padding: 10px 20px;
    margin: 5px;
    border-radius: 5px;
    cursor: pointer;
    text-decoration: none;
    font-size: 15px;
    font-family: inherit;
  }
  .btn:focus{
    outline: none;
  }
</style>
