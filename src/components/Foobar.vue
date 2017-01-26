<!--
    Foobar does nothing but make a box jump on click one time
-->

<template>
    <div id="foobar">
        <h3>animation playground</h3>
        <div class="container" @click="isJumping = true">
            <div class="foobar" v-bind:class="{jump : isJumping}"></div>
        </div>
    </div>
</template>
<script>
export default{
    name: 'foobar',
    data(){
        return {
            isJumping: false
        }
    },
    methods: {}
}

</script>

<style>
    .container {
        height: 200px;
        width: 30px;
        border: 1px solid maroon;
        position: relative;
    }
    .foobar {
      position: absolute;
      height: 30px;
      width: 30px;
      background-color: #5F396A;
      bottom: 0;
      left: 0;
    }
    .jump {
        -webkit-animation: jump 2s;
        animation: jump 2s;
    }
    @-webkit-keyframes jump {
      0%  { transform: translateY(0); }
      50% { transform: translateY(-100px); }
      100% { transform: translateY(0); }
    }
</style>
