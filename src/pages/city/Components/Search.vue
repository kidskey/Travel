<template>
<div>
    <div class="search">
        <input class="search-input" type="text" v-model="keyword" placeholder="输入城市名或拼音">
    </div>
    <div class="search-content" ref="search" v-show="keyword">
        <ul>
            <li class="search-item border-bottom" v-for="item in list" :key="item.id" @click="handleCity(item.name)">{{item.name}}</li>
            <li class="search-item border-bottom" v-show="hasNoData">没有找到匹配数据</li>
        </ul>
    </div>
</div> 
    </template>

    
<script>
    import BScroll from "better-scroll"
    import { mapMutations } from 'vuex'

    export default{
        name:'CitySearch',
        props:{
            ct:Object
        },
        data(){
            return {
                keyword:'',
                list:[],
                timer:null
            }
        },
        computed:{
            hasNoData(){
                return !this.list.length
            }
        },
        methods:{
            handleCity(city){
                // this.$store.commit('changeCity', city)
                this.changeCity(city)
                this.$router.push('/')
            },
            ...mapMutations(['changeCity'])
        },
        watch:{
            keyword(){
                if(this.timer){
                    clearTimeout(this.timer)
                }
                if(!this.keyword){
                    this.list = []
                    return
                }
                this.timer =  setTimeout(()=>{
                    const result = []
                    for(let i in this.ct){
                        this.ct[i].forEach( (val) => {
                            if(val.spell.indexOf(this.keyword) != -1 || val.name.indexOf(this.keyword) != -1){
                                result.push(val)
                            }
                        });
                    }
                    this.list = result
                },100)
            }
        },
        mounted(){
            this.scroll = new BScroll(this.$refs.search);
        }
    }
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'

    .search 
        height: .7rem
        background: $bgColor
        padding: 0 .1rem
        .search-input
            height: .6rem
            line-height: .6rem
            width: 100%
            text-align: center
            border-radius: 0.06rem
            color: #666
            padding: 0 .1rem
            box-sizing: border-box
    .search-content
        position: absolute
        top: 1.58rem
        left: 0
        right: 0
        bottom: 0
        overflow: hidden
        background: #eee
        z-index: 1
        .search-item
            line-height: .62rem
            padding-left: .2rem
            color: #666
            background: #fff
</style>
