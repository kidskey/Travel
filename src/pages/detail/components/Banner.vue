<template>
    <div>
        <div class="banner" @click="handleBanner">
            <img class="banner-img" src="//img1.qunarzz.com/sight/p0/1507/9e/7b5e0a44cb0310280b1aeb2a8dd94de8.water.jpg_600x330_bfb39f14.jpg" alt="">
            <div class="banner-info">
                <div class="banner-title">长隆国际大马戏剧院</div>
                <div class="banner-number"><span class="iconfont banner-icon">&#xe692;</span>87</div>
            </div>
        </div>
        <common-gallery :imgs="imgs" v-show="showGallery" @close="handleGalleryClose"></common-gallery>
    </div>
    
</template>
<script>
    import CommonGallery from 'common/gallery/Gallery'

    export default{
        name:"DetailBanner",
        components:{
            CommonGallery
        },
        data(){
            return{
                showGallery:false,
                imgs:['https://imgs.qunarzz.com/sight/p0/1502/da/dac02fc8e4d9f3d2.water.jpg_r_800x800_1fa313ea.jpg',
                    'https://imgs.qunarzz.com/sight/p0/1502/1d/1d16998cee49f904.water.jpg_r_800x800_3d6ca48d.jpg']
            }
        },
        methods:{
            handleBanner(){
                this.showGallery = true
            },
            handleGalleryClose(){
                this.showGallery = false
            }
        }
    }
</script>
<style lang="stylus" scoped>
    .banner
        position:relative
        overflow:hidden
        height:0
        padding-bottom:55%
        .banner-img
            width: 100%
        .banner-info
            position:absolute
            left:0
            right:0
            bottom:0
            line-height: .6rem
            display:flex
            color: #fff
            background-image: linear-gradient(top,rgba(0,0,0,0),rgba(0,0,0,.8))
            .banner-title
                flex:1
                font-size: .32rem
                padding: 0 .2rem
            .banner-number
                margin-top: .14rem
                padding:0 .3rem
                line-height: .32rem
                height: .32rem
                border-radius: .2rem
                background: rgba(0,0,0, .8)
                font-size: .24rem
                .banner-icon
                    font-size: .24rem
                    padding-right: .1rem
</style>
