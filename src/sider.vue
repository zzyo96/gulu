<template>
    <transition name="slide">
        <div class="sider" v-if="visible">
            <slot></slot>
            <button @click="visible=false">隐藏</button>
        </div>
    </transition>
</template>
<script>
    export default {
        name:'GuluSider',
        data(){
            return {
                visible:true
            }
        }
    }
</script>
<style lang="scss" scoped>
    .sider{
        position: relative;
        background: rgb(255,97,56);
        width: 200px;
        & > button{
            position: absolute;
            top:0;
            right:0;
        }
    }
    .slide-enter-active, .slide-leave-active {
        transition: all 0.3s linear;
    }
    .slide-enter, .slide-leave-to{
        margin-left: -200px;
    }
</style>