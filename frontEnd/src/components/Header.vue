<template>
    <header>
        <!-- <h2>Task Tracker</h2> -->
        <h1>{{ title }}</h1>
        <Button text="Add Task" color="green"/>
    </header>
</template>

<script>
import Button from './Button.vue'

export default {
    name: 'header',
    props: {
        title: String,
    },
    components: {
        Button
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