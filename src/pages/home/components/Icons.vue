<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page,index) in pages" :key="index">
                <ul>
                    <li class="icon" v-for="item in page" :key="item.id">
                        <div class="icon-image">
                            <img :src="item.imgUrl" class="icon-img">
                        </div>
                        <p class="icon-desc">{{item.desc}}</p>
                    </li>
                </ul>
            </swiper-slide>
        </swiper>
    </div>
</template>
<script>
    export default{
        name:'HomeIcons',
        props:{
            icon: Array
        },
        data(){
            return {
                swiperOption:{
                    autoplay: false
                }
            }
        },
        computed:{
            pages(){
                const pages = []
                this.icon.forEach((item,index)=>{
                    const page = Math.floor(index / 8)
                    if(!pages[page]){
                        pages[page] = []
                    }
                    pages[page].push(item);
                })
                return pages;
            }
        }
    }
    
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'
    @import '~styles/mixin.styl'
    
    .icons >>> .swiper-container
        height: 0 
        padding-bottom: 50%
        background: #fff 
    .icons 
        margin-top: .1rem
        .icon
            width: 25%
            float: left 
            padding-bottom: 25%
            text-align: center
            overflow: hidden 
            position: relative
            height: 0
            .icon-image
                position: absolute 
                top: 0 
                left: 0
                right: 0
                bottom: .44rem
                box-sizing: border-box
                padding: .1rem
                .icon-img
                    height: 100%
            .icon-desc
                position: absolute 
                left: 0
                right: 0
                bottom: 0
                line-height: .44rem
                color: $darkTextColor
                ellipsis()
</style>
