<template>
    <div class="icons">
        <swiper :options="swiperOption">
            <swiper-slide v-for="(page,index) in pages" :key="index">
                <ul>
                    <li class="icon" v-for="item in page" :key="item.id">
                        <div class="icon-image">
                            <img :src="item.imgUrl" class="icon-img">
                        </div>
                        <p class="icon-desc">{{item.text}}</p>
                    </li>
                </ul>
            </swiper-slide>
        </swiper>
    </div>
</template>
<script>
    export default{
        name:'HomeIcons',
        data(){
            return {
                swiperOption:{
                    loop: false
                },
                iconList:[
                    {
                        id:1,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/95/f3dd6c383aeb3b02.png',
                        text:"景点门票"
                    },
                    {
                        id:2,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/ff/fdf170ee89594b02.png',
                        text:"北京必游"
                    },
                    {
                        id:3,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/6a/45f595250c73d102.png',
                        text:"夏日玩水"
                    },
                    {
                        id:4,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/20/831d62d2e1c7be02.png',
                        text:"文化古迹"
                    },
                    {
                        id:5,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/76/eb88861d78fb9902.png',
                        text:"动植物园"
                    },
                    {
                        id:6,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1803/6c/9e54a8540fee0102.png',
                        text:"故宫"
                    },
                    {
                        id:7,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/5a/13ceb38dcf262f02.png',
                        text:"一日游"
                    },
                    {
                        id:8,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/95/8d02011d149bdb02.png',
                        text:"汽车票"
                    },
                    {
                        id:9,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1804/95/8d02011d149bdb02.png',
                        text:"汽车票"
                    }
                ]
            }
        },
        computed:{
            pages(){
                const pages = []
                this.iconList.forEach((item,index)=>{
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
