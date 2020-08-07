<template>
    <div class="gradient">
        <gradient-color
                v-for="(todo,index) in todos"
                :key="todo.name"
                :colors="todo.colors"
                :active="index <= currentIndex"
        />
    </div>
</template>

<script>
    import {mapState} from 'vuex';
    import gradientColor from "./gradientClolor";


    export default {
        name: "gradient",
        components:{
            gradientColor,
        },
        computed:{
            ...mapState(['todos','currentIndex'])
        }
    }
</script>

<style scoped>
    .gradient {
        position: fixed;
        top: 0;
        bottom: 0;
        left: 0;
        right: 0;
        z-index: -1;
    }
</style>