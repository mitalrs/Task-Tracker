<template>
    <div @dblclick="$emit('toggle-reminder', task.id)" :class="[task.reminder ? 'reminder' : '', 'task']">
        <h3>{{task.text}}
            <button class="button-dlt" @click="$emit('delete-task',task.id)">
                <i class="fa-solid fa-trash"></i>
            </button>
        </h3>
        <p>{{task.day}}</p>
    </div>
</template>


<script>
export default {
    name: 'Task',
    props: {
        task: Object,
    }
}
</script>



<style scope>
.fas{
    color: #d85c5c;
}

.task{
    background-color: #292e30;
    margin: 5px;
    padding: 10px 20px;
    cursor: pointer;
    color: #b6c2dc;
}
 .task.reminder{
    border-left: 5px solid #4682b6;
 }

 .task h3{
    display: flex;
    align-items: center;
    justify-content: space-between;
 }
 .button-dlt{
    background-color: transparent;
    border: none;
    color: #d85c5c;
    font-size: 20px;
 }
 
</style>