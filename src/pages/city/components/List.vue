<template>
    <div class="list" ref="wrapper">
        <div>
            <div class="area">
                <div class="title border-topbottom">当前城市</div>
                <div class="button-list">
                    <div class="button-wrapper">
                        <div class="button">{{this.currentCity}}</div>
                    </div>
                </div>
            </div>
            <div class="area">
                <div class="title border-topbottom">热门城市</div>
                <div class="button-list">
                    <div class="button-wrapper" v-for="item in hct" :key="item.id"
                    @click="handleCity(item.name)">
                        <div class="button">{{item.name}}</div>
                    </div>
                </div>
            </div>
            <div class="area" 
                v-for="(item,key) in ct" 
                :key="key" :ref="key">
                <div class="title border-topbottom">{{key}}</div>
                <ul class="item-list">
                    <li class="item border-bottom" v-for="innerItem in item" 
                    :key="innerItem.id" @click="handleCity(innerItem.name)">
                        {{innerItem.name}}
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>
<script>

    import BScroll from 'better-scroll'
    import {mapState, mapMutations} from 'vuex'

    export default{
        name:'CityList',
        props:{
            ct: Object,
            hct: Array,
            letter: String
        },
        data(){
            return {

            }
        },
        computed:{
            ...mapState({
                currentCity:'city'
            })
        },
        methods:{
            handleCity(city){
                // this.$store.commit('changeCity', city)
                this.changeCity(city)
                this.$router.push('/')
            },
            ...mapMutations(['changeCity'])
        },
        mounted(){
            this.scroll = new BScroll(this.$refs.wrapper)
        },
        watch:{
            letter(){
                if(this.letter){
                    const element = this.$refs[this.letter][0]
                    this.scroll.scrollToElement(element)
                }
            }
        }
    }
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'

    .border-topbottom
        &:before
            border-color: #ccc
        &:after
            border-color: #ccc

    .border-bottom
        &:before
            border-color: #ccc
    .list
        position: absolute 
        top: 1.56rem
        left: 0
        right: 0
        bottom: 0
        overflow: hidden
        .title
            line-height: .54rem
            background: #eee
            padding-left: .2rem
            color: #666
            font-size: .26rem
        .button-list
            padding: .1rem .6rem .1rem .1rem
            overflow:hidden
            .button-wrapper
                float: left
                width: 33.3%
                .button
                    margin: .1rem
                    text-align: center
                    border: .02rem solid #ccc
                    padding: .1rem 0
                    border-radius: .06rem
        .item-list
            .item
                line-height: .76rem
                padding-left: .2rem
</style>
