<template>
    <button @click="onClick()" :style="{background: color}" class="btn">{{text}}</button>
</template>

<script>
export default {
    name: 'Button',
    props: {
        text: String,
        color: String,
    },
    methods: {
        onClick() {
            this.$emit('btn-click')
        },
    },
}
</script>

<style scoped>
button{
    border-style: none;
    border-radius: 5px;
    height: 40px;
    width: 110px;
    font-weight: 500;
    font-size: 20px;
}
</style>