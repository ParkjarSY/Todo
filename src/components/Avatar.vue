<template>
<!--    文字内容-->
    <div class="avatar" :class="{ avatar_select: !!selected}">
        <div class="logo">
            <img src="" alt="">
        </div>
        <h2 class="name">Hello,{{names}}</h2>
        <p class="tips">
            你还有<b>{{todayTasks.length}}</b>件事情<br/>需要去做
        </p>
        <p class="date">日期:今天是{{today  | dataString }}</p>
    </div>
</template>

<script>
    import {mapState,mapGetters} from 'vuex'
    export default {
        name: "Avatar",
        props:{
            names:{
                type:String,
                default:'PJC'
            }
        },
        data (){
          return{
              today:new Date()
          }
        },
        computed:{
            ...mapState(['selected']),
            ...mapGetters(['todayTasks']),
        },
        filters:{
            dataString(num){
                return num.toDateString().toUpperCase().replace(/(\s\d{2})$/,', $1')
            }
        }
    }
</script>

<style lang="scss">
    .avatar{
        display:flex;
        padding:0 40px;
        height: 300px;
        justify-content: flex-end;
        flex-direction: column;
        transition: all 0.6s ease;
    }
    .avatar_select{
        transform: translate3d(0,20px,0);
        opacity: 0;
    }
    .logo{
        width: 44px;
        height: 44px;
        border-radius: 100%;
        overflow: hidden;
        box-shadow: 0 6px 10px rgba(0,0,0,0.2);

        img{
            display: block;
            width: 100%;
            height: 100%;
        }
    }
    .name{
        margin-top: 32px;
        padding:0 6px;
        font-size: 32px;
        letter-spacing: 1px;
        font-weight: 300;
    }
    .tips{
        margin-top: 16px;
        padding: 0 6px;
        font-size: 13px;
        font-weight: 100;
        opacity: 0.8;
        line-height: 1.6em;
    }
    .date{
        margin-top: 44px;
        margin-bottom: 16px;
        padding: 0 6px;
        font-size: 14px;
    }
</style>