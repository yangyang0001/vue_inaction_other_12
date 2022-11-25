
<template>
    <div class="root">
        <h1>App根组件</h1>
        <a href="#/home">首页</a>   &nbsp;&nbsp;
        <a href="#/movie">电影</a>  &nbsp;&nbsp;
        <a href="#/about">关于</a>

        <hr/>

        <component :is="component_id"></component>

    </div>
</template>

<script>
import Home from '@/components/Home.vue'
import Movie from '@/components/Movie.vue'
import About from '@/components/About.vue'


export default {

    components: {
        Home,
        Movie,
        About
    },

    data: function () {
        return {
            component_id: ''
        }
    },

    created() {
        // 监听 window 对象的 onhashchange 事件
        window.onhashchange = () => {
            console.log('监听到hash地址变化为', location.hash);
            if(location.hash === '#/home') {
                this.component_id = 'Home';
            } else if(location.hash === '#/movie') {
                this.component_id = 'Movie';
            } else if (location.hash === '#/about') {
                this.component_id = 'About';
            } else {
                this.component_id = '';
            }
        }
    },

    methods: {

    },

}
</script>

<style lang="less" scoped>
.root {
    padding: 5px 20px 260px 20px;
    background-color: #b9bdb0;
}
</style>