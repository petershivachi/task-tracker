<template>
 <div class="container">
   <Header title="Task Tracker" />
   <Tasks
   @toggle-task="toggleTask"
   @delete-task="deleteTask" :tasks="tasks"/>
 </div>
</template>

<script>
import Header from './components/Header.vue';
import Tasks from './components/Tasks.vue';

export default {
  name: 'App',
  components: {
   Header,
   Tasks
  },

  data() {
    return {
      tasks: []
    }
  },

  methods: {
    deleteTask(id){
    if(confirm('Are you sure')){
        this.tasks = this.tasks.filter((task) => task.id !== id)
    }
    },

    toggleTask(id){
      this.tasks = this.tasks.map((task) => 
        task.id === id ? {...task, reminder: !task.reminder} : task
      )
    }
  },

  created() {
    this.tasks = [
      {
        id: 1,
        text: 'Visit the dentist',
        day: 'March 11th at 2.30pm',
        reminder: true
      },
       {
        id: 2,
        text: 'Visit a local childrens home',
        day: 'March 12th at 3.30pm',
        reminder: false
      },
       {
        id: 3,
        text: 'Go balling with Friends',
        day: 'March 11th at 4.30pm',
        reminder: true
      },
       {
        id: 4,
        text: 'Leg day',
        day: 'March 13th at 5.30pm',
        reminder: false
      },
       {
        id: 5,
        text: 'March 11th at 6.30pm',
        day: 'March 15th at 2.30pm',
        reminder: true
      }
    ]
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins&display=swap');

* {
  box-sizing:  border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: 'Poppins', sans-serif;
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
  cursor: pointer;
  text-decoration: none;
  font-size: 15px;
  font-family: inherit;
}

.btn:focus {
  outline: none;
}

.btn:active {
  transform: scale(0.98);
}

.btn-block {
  display: block;
  width: 100%;
}
</style>
