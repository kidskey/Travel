<template>
    <div class="search">
        <input class="search-input" type="text" placeholder="输入城市名或拼音">
    </div>
</template>
<script>
    export default{
        name:'CitySearch',
        data(){
            return {

            }
        }
    }
</script>
<style lang="stylus" scoped>
    @import '~styles/varibles.styl'

    .search 
        height: .7rem
        background: $bgColor
        padding: 0 .1rem
        .search-input
            height: .6rem
            line-height: .6rem
            width: 100%
            text-align: center
            border-radius: 0.06rem
            color: #666
            padding: 0 .1rem
            box-sizing: border-box
</style>
