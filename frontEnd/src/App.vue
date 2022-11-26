<script>
   import Header from './components/Header.vue'
   import Tasks from './components/Tasks.vue'
   import AddTask from './components/AddTask.vue'

export default {
  name: 'App',
  components: {
    Header,
    Tasks,
    AddTask,
  },
  data(){
    return {
      tasks: [],
      showAddTask: false
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    },
    addTask(task){
      this.tasks = [...this.tasks, task]
    },
    deleteTask(id){
      if(confirm('Are you sure to delete?')){
        this.tasks = this.tasks.filter((task)=> task.id !== id) 
      }
    },
    toggleReminder(id){
      this.tasks = this.tasks.map((task)=> task.id === id ? {...task, reminder: !task.reminder } : task 
      )
    },
    async fetchTasks(){
      const res = await fetch('api/tasks')

      const data = await res.json()

      return data
    },
    async fetchTask(id){
      const res = await fetch(`api/tasks/${id}`)

      const data = await res.json()

      return data
    },
  },
   async created(){
    this.tasks= await this.fetchTasks()
  }
}
</script>

<template>
  <div class="container">
    <!-- <h1>hello word</h1> -->
  <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
  <div v-show="showAddTask">
    <AddTask @add-task="addTask"/>
  </div>
  <Tasks @toggle-reminder="toggleReminder" @delete-task="deleteTask" :tasks="tasks" />
  </div>
</template>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}
body{
  widows: 100vw;
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
