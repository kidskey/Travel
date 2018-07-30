<template>
    <div class="wrapper">
        <swiper :options="swiperOption">
            <!-- slides -->
            <swiper-slide v-for="item in swiperList" :key="item.id">
                <img class="swiper-image" :src='item.imgUrl'>
            </swiper-slide>
            
            <!-- Optional controls -->
            <div class="swiper-pagination"  slot="pagination"></div>
        </swiper>
    </div>
</template>
<script>
    export default {
        name:'HomeSwiper',
        data(){
            return {
                swiperOption:{
                    pagination:'.swiper-pagination',
                    loop: true,
                    autoplay : 3000,
                    speed: 500,
                    autoplayDisableOnInteraction: false

                },
                swiperList:[
                    {
                        id:1,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1807/c6/44fce1467be17702.jpg_750x200_406f5fc3.jpg'
                    },
                    {
                        id:2,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1807/66/e5a5cec881702f02.jpg_750x200_67bb5691.jpg'
                    },
                    {
                        id:3,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1806/8f/d09fa241a01ac02.jpg_750x200_e0c86013.jpg'
                    },
                    {
                        id:4,
                        imgUrl:'http://img1.qunarzz.com/piao/fusion/1807/e7/d70d0830a9941b02.jpg_750x200_f8c7d2ad.jpg'
                    }
                ]
            }
        }
    }
</script>
<style lang="stylus" scoped>
    .wrapper >>> .swiper-pagination-bullet-active
        background: #fff
    .wrapper
        width: 100%
        height: 0
        overflow: hidden
        padding-bottom: 26%
        background: #eee
        .swiper-image
            width: 100%
</style>
