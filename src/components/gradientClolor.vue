<template>
    <div
            class="gradient_color"
            :class="{ g_color_active: active }"
            :style="{ backgroundImage: gradientColor }"
    />
</template>

<script>
    export default {
        props: {
            colors: {
                type: Array
            },
            active: {
                type: Boolean
            }
        },
        computed: {
            // 用来获取颜色
            gradientColor () {

                const colorBottom = `color-stop(30%, ${this.colors[0]})`
                const colorTop = `to(${this.colors[1]})`
               //改变背景颜色
                return `-webkit-gradient(linear, left bottom, left top, ${colorBottom}, ${colorTop})`
            }
        }
    }
</script>

<style lang="scss">
    .gradient_color {
        position: absolute;
        width: 100%;
        height: 100%;
        opacity: 0;
        transition: opacity 0.5s ease;

    }
    .g_color_active {
        opacity: 1;
    }

</style>
