<template>
    <transition name="grow">
        <button
                class="floating_button"
                v-if="!!selected"
                :class="{'f_button_editing': !!editing}"
                :style="{background:gradientColor}"
                @click="toggleEditing"
        ></button>
    </transition>
</template>

<script>
    import {mapState,mapGetters,mapMutations} from 'vuex'
    export default {
        name: "floatButton",
        computed:{
            //使用vuex
            ...mapState(['selected',"editing"]),
            ...mapGetters(["currentTodo"]),
            gradientColor(){
                //渐变色
                const colorLeft = `color-stop(30%,${this.currentTodo.colors[0]})`
                const colorRight = `to(${this.currentTodo.colors[1]})`
                return `-webkit-gradient(linear,left bottom,right top,${colorLeft},${colorRight})`
            }
        },
        // 将输入的内容传递至vuex进行操作
        methods:{
            ...mapMutations(['toggleEditing'])
        }
    }
</script>

<style lang="scss">
    .floating_button{
        position: fixed;
        right: 44px;
        bottom: 64px;
        margin: 0;
        padding: 0;
        border: none;
        outline: none;
        border-radius: 44px;
        width: 44px;
        height: 44px;
        color: white;
        box-shadow: 0 5px 10px rgba(0, 0, 0, 0.2);
        transition: all 0.5s ease;
    }
    .floating_button::before,
    .floating_button::after{
        content: '';
        position: absolute;
        top: 50%;
        left: 50%;
        display: block;
        width: 20px;
        height: 2px;
        background-color: white;
        transform: translate(-50%, -50%);
    }
    .floating_button::after{
        transform: translate(-50%,-50%) rotate(90deg);
    }
    .f_button_editing{
        right: 0;
        bottom: 0;
        width: 100%;
        border-radius: 0;
    }
    .grow-leave-to,
    .grow-enter{
        transform: scale(0);
    }
    .grow-enter-to,
    .grow-leave{
       transform: scale(1);
    }
    .grow-enter-active{
        transition: all 0.2s 0.3s ease;
    }
    .grow-leave-active{
        transition: all 0.3s ease;
    }
</style>