<template>
    <div>
        <div class="title">周末去哪儿</div>
        <ul>
            <li class="item border-bottom" v-for="item in wk" :key="item.id">
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
        props:{
            wk: Array
        },
        data(){
            return {
              
            }
        }
    }
</script>
<style lang="stylus" scoped>
    @import '~styles/mixin.styl'

    .title
        line-height: 0.8rem
        background: #eee
        text-indent: 0.2rem
    .item-image-wrapper
        height: 0
        overflow: hidden 
        padding-bottom: 38%
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
