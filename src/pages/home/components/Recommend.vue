<template>
    <div>
        <div class="title">热销推荐</div>
        <ul>
            <li class="item border-bottom" v-for="item in recommendList" :key="item.id">
                <img class="item-image" :src="item.imgUrl" alt="">
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                    <button class="item-btn">查看详情</button>
                </div>
            </li>
        </ul>
    </div> 
</template>
<script>
    export default {
        name:'HomeRecommend',
        data(){
            return {
                recommendList:[
                    {
                        title:"上海玛雅海滩水公园",
                        imgUrl:"http://img1.qunarzz.com/sight/p0/1506/30/7a528fae12c17e6e29d5d13a9d9813ee.water.jpg_200x200_e7f0d0ad.jpg",
                        desc:"Welcome",
                        id:1
                    },
                    {
                        title:"上海欢乐谷",
                        imgUrl:"http://img1.qunarzz.com/sight/p0/1609/80/8092254b7f5f016ea3.water.jpg_200x200_cd798d39.jpg",
                        desc:"Welcome",
                        id:2
                    },
                    {
                        title:"上海迪士尼乐园",
                        imgUrl:"http://img1.qunarzz.com/sight/p0/1607/7c/7cda8b6782dabd80b4.img.jpg_200x200_2039e660.jpg",
                        desc:"Welcome",
                        id:3
                    },
                    {
                        title:"上海科技馆",
                        imgUrl:"http://img1.qunarzz.com/sight/p0/1411/4f/146031f0bc5d7e0dd960d3f5bf0c9eca.water.jpg_200x200_f22705c9.jpg",
                        desc:"Welcome",
                        id:4
                    }
                ]
            }
        }
    }
</script>
<style lang="stylus" scoped>
    @import '~styles/mixin.styl'

    .title
        margin-top: 0.2rem
        line-height: 0.8rem
        background: #eee
        text-indent: 0.2rem
    .item
        display: flex
        height: 1.9rem
        overflow: hidden
        min-width: 0
        .item-image
            width: 1.7rem
            height: 1.7rem
            padding: 0.1rem
        .item-info
            flex: 1
            padding: 0.1rem
            .item-title
                line-height: .54rem
                font-size: .32rem
                ellipsis()
            .item-desc
                line-height: .4rem
                color: #ccc
                ellipsis()
            .item-btn
                line-height: .4rem
                background: #ff9300
                padding: 0 0.2rem
                border-radius: .06rem
                margin-top: .3rem
                color: #fff
</style>
