<template>
    <div>
        <div class="title">周末去哪儿</div>
        <ul>
            <li class="item border-bottom" v-for="item in recommendList" :key="item.id">
                <div class="item-image-wrapper">
                    <img class="item-image" :src="item.imgUrl" alt="">
                </div>
                <div class="item-info">
                    <p class="item-title">{{item.title}}</p>
                    <p class="item-desc">{{item.desc}}</p>
                </div>
            </li>
        </ul>
    </div> 
</template>
<script>
    export default {
        name:'HomeWeekend',
        data(){
            return {
                recommendList:[
                    {
                        title:"上海必游TOP10",
                        imgUrl:"http://img1.qunarzz.com/sight/source/1505/7d/df6ff468331c43.jpg_r_640x214_1f3783d0.jpg",
                        desc:"中西合璧，现代和传统各有各的精彩",
                        id:1
                    },
                    {
                        title:"亲子时光TOP10",
                        imgUrl:"http://img1.qunarzz.com/sight/source/1603/ad/69b0fc5f48ad5f.jpg_r_640x214_b0fd5c7b.jpg",
                        desc:"走进自然或玩转乐园，感知大千世界",
                        id:2
                    },
                    {
                        title:"上海城市观光",
                        imgUrl:"http://img1.qunarzz.com/sight/source/1511/1d/fe098e8cfec117.jpg_r_640x214_a9be292a.jpg",
                        desc:"来这里寻找你所认识的上海",
                        id:3
                    },
                    {
                        title:"戏水清凉一夏",
                        imgUrl:"http://img1.qunarzz.com/sight/source/1505/6f/2711e071838590.jpg_r_640x214_8f1ad9a1.jpg",
                        desc:"夏日戏水，玩“乐”无穷",
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
    .item-image-wrapper
        height: 0
        overflow: hidden 
        padding-bottom: 33%
        .item-image
            width: 100%
    .item-info
        padding: 0.1rem
        .item-title
            line-height: .54rem
            font-size: .32rem
            ellipsis()
        .item-desc
            line-height: .4rem
            color: #ccc
            ellipsis()
</style>
