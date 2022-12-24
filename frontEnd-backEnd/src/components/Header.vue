<template>
    <header>
        <!-- <h2>Task Tracker</h2> -->
        <!-- <h1>{{ title }}</h1> -->
        <LogoVue />
        <Button v-show="homePage"
         @btn-click="$emit('toggle-add-task')"
         :text="showAddTask ? 'x' : '+'" 
         :color="showAddTask ? '#d85c5c' : '#4682b6'"
         />
    </header>
</template>

<script>
import Button from './Button.vue'
import LogoVue from './Logo.vue'

export default {
    name: 'header',
    props: {
        title: String,
        showAddTask: Boolean,
    },
    components: {
        Button,
        LogoVue
    },
    computed: {
        homePage() {
            if(this.$route.path === '/'){
                return true
            } else{
                return false
            }
        }
    }
}
</script>

<style scoped>
 header{
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 20px;
 }
</style>