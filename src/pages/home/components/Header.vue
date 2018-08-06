<template>
    <div class="header">
        <div class="header-left">
            <div class="iconfont">&#xe624;</div>
        </div>
        <div class="header-input">
            <span class="iconfont">&#xe632;</span>
            输入城市/景点/游玩主题
        </div>
        <router-link to="/city">
            <div class="header-right">
                {{this.city}}
                <span class="iconfont arrow-icon">&#xe64a;</span>
            </div>
        </router-link>
    </div>
</template>
<script>
    import {mapState} from 'vuex'
    export default{
        name:'HomeHeader',
        data(){
            return {

            }
        },
        computed:{
            ...mapState(['city'])
        }
    }
    
</script>
<style lang="stylus" scoped>
    // @import '../../../assets/styles/varibles.styl'
    @import '~styles/varibles.styl'

    .header
        display: flex
        line-height: .86rem
        background: $bgColor
        color: #fff
        font-size: 0
        .header-left
            width: .64rem
            float: left
            text-align: center
        .header-input
            line-height: .64rem
            height: .64rem
            flex: 1
            background: #fff
            border-radius: .1rem
            margin-top: .12rem
            margin-left: .2rem
            color: #ccc
            padding-left: .2rem
            font-size: .32rem
        .header-right
            font-size: .3rem
            min-width: 1.04rem
            padding: 0 .1rem
            float: right
            text-align: center
            color: #fff
            .arrow-icon
                font-size: .3rem
                margin-left: -0.05rem

</style>
