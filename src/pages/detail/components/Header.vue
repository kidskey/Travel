<template>
    <div>
        <router-link tag="div" to="/" class="header-abs" v-show="showAbs">
            <div class="iconfont back-icon">&#xe624;</div>
        </router-link>
        <div class="header-fixed" v-show="!showAbs" :style="opacityStyle">
            <router-link to="/">
                <div class="iconfont header-fixed-back">&#xe624;</div>
            </router-link>
            景点详情
        </div>
    </div>
</template>
<script>

    export default{
        name:"DetailHeader",
        data(){
            return{
                showAbs: true,
                opacityStyle:{
                    opacity:0
                }
            }
        },
        methods:{
            handleScroll(){
                const top = document.documentElement.scrollTop
                if( top > 60 ){
                    this.showAbs = false
                    let opacity = top / 140
                    opacity = opacity > 1 ? 1: opacity
                    this.opacityStyle = {
                        opacity
                    }
                }else{
                    this.showAbs = true
                }
            }
        },
        activated(){
            window.addEventListener('scroll',this.handleScroll)
        },
        deactivated(){
            window.removeEventListener('scroll',this.handleScroll)
        }
    }
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'

   .header-abs
        position:absolute
        left: .2rem
        top: .2rem
        width: .8rem
        height: .8rem
        text-align: center
        line-height:.8rem
        border-radius: .4rem
        background: rgba(0,0,0,.8)
        .back-icon
            color: #fff
            font-size: .4rem
    .header-fixed
        height:.86rem 
        line-height: .86rem
        color: #fff
        text-align: center
        background: $bgColor
        font-size: .3rem
        position: fixed
        top: 0
        left: 0
        right: 0
        z-index: 99
        .header-fixed-back
            width: .64rem
            text-align: center
            font-size: .4rem
            position: absolute
            top: 0
            left: 0
            color: #fff
</style>
