<script>
   import Header from './components/Header.vue'
   import Footer from './components/Footer.vue'
  
  //  import * as dotenv from 'dotenv'
  

export default {
  name: 'App',
  components: {
    Header,
    Footer
  },
  data(){
    return {
      showAddTask: false,
    }
  },
  methods: {
    toggleAddTask(){
      this.showAddTask = !this.showAddTask
    }
  },
}
</script>

<template>
  <div class="container">
    <!-- <h1>hello word</h1> -->
  <Header @toggle-add-task="toggleAddTask" title="Task Tracker" :showAddTask="showAddTask" />
  
  <router-view :showAddTask="showAddTask"></router-view>
  <Footer/>
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
