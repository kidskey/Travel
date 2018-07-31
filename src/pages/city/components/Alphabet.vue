<template>
    <ul class="list">
        <li class="item" v-for="(item,key) in ct" :key="key">{{key}}</li>
    </ul>
</template>
<script>

    export default{
        name:'CityAlphabet',
        props:{
            ct: Object
        },
        data(){
            return {

            }
        }
    }
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'

    .list
        position: absolute
        top: 1.58rem
        right: 0
        bottom: 0
        width: .4rem
        display:flex
        flex-direction: column
        justify-content: center
        .item
            text-align: center
            line-height: .4rem
            color: $bgColor
</style>
