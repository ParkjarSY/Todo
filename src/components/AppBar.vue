<template>
    <div class="app-bar">
        <span class="app_bar_l" @click="$emit('leftClick')">
            <i :class="['fa',`fa-${left}`]"></i>
        </span>
        <h1>{{title}}</h1>
        <span class="app_bar_r" @click="$emit('rightClick')">
            <i :class="['fa',`fa-${right}`]"></i>
        </span>
    </div>
</template>

<script>

    export default {
        name: "AppBar",
        props:{
            title:{
                type:String,
                default:''
            },
            left: {
                type: String,
                default: 'c_left'
            },
            right:{
                type:String,
                default:'ellipsis_v'
            }
        }
    }
</script>

<style lang="scss">
    .app-bar {
        display: flex;
        align-items: center;
        height: 44px;
        font-size: 15px;
        z-index: 1;
        /*background-color: black;*/
        h1{
            display: flex;
            justify-content: center;
            flex: 1;
        }
        span{
            padding: 0 20px;
        }
    }
</style>