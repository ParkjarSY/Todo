<template>
    <div class="todo_list" :class="{'t_list_selected': !!selected}">
        <ul :style="{width:`${todos.length*100}%`}" >
            <li
                    v-for="todo in todos"
                    :key="todo.name"
                    :style="{ transform: `translate3d(-${currentIndex * 100}%, 0, 0)` }"
            >
                <todo
                        :todo="todo"
                        :selected="selected && todo === selected.todo"
                        @select="selectTodo"
                />
            </li>
        </ul>
    </div>
</template>

<script>
    import {mapState,mapMutations} from 'vuex'
    import Todo from "./Todo";
    export default {
        name: "todoList",
        components:{
            Todo,
        },

        mounted() {
            let touch = {}
            this.$el.addEventListener('touchstart',e =>{
                touch.startX = e.touches[0].clientX
                touch.endX = 0
            })
            this.$el.addEventListener('touchmove', e => {
                touch.endX = e.touches[0].clientX
            })
            this.$el.addEventListener('touchend',()=>{
                if (!touch.endX || Math.abs(touch.endX - touch.startX) < 10 ){
                    return
                }
                if (touch.endX <touch.startX){
                    this.nextTodo()
                }else {
                    this.prevTodo()
                }
            })
        },
        computed: {
            ...mapState(['todos', 'currentIndex', 'selected'])
        },
        methods: {
            ...mapMutations(['selectTodo','nextTodo','prevTodo'])
        },

    }
</script>

<style lang="scss">
    .todo_list {
        padding: 0 32px;
        height: 400px;
        transition: all 0.5s ease;

        > ul,
        > ul > li {
            display: flex;
            height: 100%;
        }
        > ul > li {
            flex: 1;
            transition: transform 0.5s ease;
        }
        .todo {
            border-radius: 8px;
            background-color: white;
        }
    }
    .t_list_selected{
        transform: scaleX(1.25);
    }
</style>