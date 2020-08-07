<template>
    <div class="home">
        <app-bar title="todo" left="bars" right="search"/>
        <avatar />
        <gradient/>
        <todo-list/>
        <todo-detail />
        <todo-editing/>
        <float-button />
    </div>
</template>

<script>
    import AppBar from '../components/AppBar'
    import Avatar from "../components/Avatar";
    import FloatButton from '../components/floatButton'
    import gradient from "../components/gradient";
    import todoDetail from "../components/todoDetail";
    import todoList from "../components/todoList";
    import TodoEditing from "../components/TodoEditing";

    export default {
        name: "home",
        components:{
            AppBar,
            Avatar,
            FloatButton,
            gradient,
            todoDetail,
            todoList,
            TodoEditing,

        },

    }
</script>

<style >
.home{
    height: 100%;
    width: 100%;
    overflow: hidden;
    color: white;
}
</style>