<template>
    <div id="app">
        <!--header-->
        <mt-header fixed title="Vue商城项目">
            <span slot="left" @click="goback" v-show="flag">
                <mt-button icon="back">返回</mt-button>
            </span>
        </mt-header>
        <!--router-view-->
        <transition>
            <router-view></router-view>
        </transition>
        <!--tabBar-->
        <nav class="mui-bar mui-bar-tab">
            <router-link class="mui-tab-item" to="/home">
                <span class="mui-icon mui-icon-home"></span>
                <span class="mui-tab-label">首页</span>
            </router-link>
            <router-link class="mui-tab-item" to="/member">
                <span class="mui-icon mui-icon-contact"></span>
                <span class="mui-tab-label">会员</span>
            </router-link>
            <router-link class="mui-tab-item" to="/cart">
                <span class="mui-icon mui-icon-extra mui-icon-extra-cart">
                    <span class="mui-badge" id="badge">{{$store.getters.getAllCount}}</span>
                </span>
                <span class="mui-tab-label">购物车</span>
            </router-link>
            <router-link class="mui-tab-item" to="/search">
                <span class="mui-icon mui-icon-search"></span>
                <span class="mui-tab-label">搜索</span>
            </router-link>
        </nav>
    </div>
</template>

<script>
    export default {
        name: 'App',
        data(){
            return {
                flag: true
            }
        },
        created(){
            this.flag = this.$route.path=='/home'?false:true
        },
        methods: {
            goback(){
                this.$router.go(-1)
            }
        },
        watch: {
            '$route.path':function (newVal) {
                if(newVal=='/home'){
                    this.flag = false
                }else {
                    this.flag=true
                }
            }
        }
        
    }
</script>

<style lang="less" scoped>
    #app {
        padding-top: 40px;
        padding-bottom: 50px;
        .mui-bar {
            box-shadow: none;
            border-top: 1px solid #ccc;
        }
        .mint-header {
            background-color: #007aff;
        }
        /*overflow-x: hidden;*/
    }
    .v-enter{
        opacity: 0;
        transform: translateX(100%);
    }
    .v-leave-to {
        opacity: 0;
        transform: translateX(-100%);
    }
    .v-enter-active,
    .v-leave-active {
        transition: all 0.5s ease;
        position: absolute;
    }
</style>
