<template>
    <div class="goodsdesc-container">
        <h3>{{info.title}}</h3>
        <hr>
        <div class="content" v-html="info.content"></div>
    </div>
</template>
<script>
    export default {
        data(){
            return {
                id: this.$route.params.id,
                info: {}
            }
        },
        created(){
            this.getGoodsDesc()
        },
        methods:{
            getGoodsDesc(){
                this.$axios.get('/api/goods/getdesc/'+this.id)
                    .then(res=>{
                        if(res.data.status===0){
                            this.info = res.data.message[0]
                        }
                    })
            }
        }
    }
</script>
<style lang="less">
    .goodsdesc-container{
        padding: 5px;
        h3{
            font-size: 14px;
            text-align: center;
            margin: 15px 0;
        }
        .content{
            
            img {
                width: 100%;
                height: auto;
                vertical-align: middle;
            }
        }
    }
</style>

