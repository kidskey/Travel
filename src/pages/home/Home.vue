<template>
    <div>
        <home-header></home-header> 
        <home-swiper :list="swiperList"></home-swiper>
        <home-icons :icon="iconList"></home-icons>
        <home-recommend :rc="recommendList"></home-recommend>
        <home-weekend :wk="weekendList"></home-weekend>
    </div>
</template>
<script>
    import HomeHeader from '@/pages/home/components/Header'
    import HomeSwiper from '@/pages/home/components/Swiper'
    import HomeIcons from '@/pages/home/components/Icons'
    import HomeRecommend from '@/pages/home/components/Recommend'
    import HomeWeekend from '@/pages/home/components/Weekend'
    import axios from 'axios'
    import { mapState } from 'vuex'


    export default {
        name:'Home',
        data(){
            return {
                swiperList:[],
                iconList:[],
                recommendList:[],
                weekendList:[],
                lastCity:''
            }
        },
        components:{
            HomeHeader,
            HomeSwiper,
            HomeIcons,
            HomeRecommend,
            HomeWeekend
        },
        computed:{
            ...mapState(['city'])
        },
        methods:{
            getHomeInfo(){
                axios.get('/api/index.json?city=' + this.city)
                .then(this.getHomeInfoSucc)
            },
            getHomeInfoSucc(res){
                res = res.data;
                if(res.ret && res.data){
                    const data = res.data
                    this.swiperList = data.swiperList
                    this.iconList = data.iconList
                    this.recommendList = data.recommendList
                    this.weekendList = data.weekendList
                }
                console.log(res);
            }
        },
        mounted(){
            this.getHomeInfo()
            this.lastCity = this.city
        },
        activated(){
            if(this.lastCity !== this.city){
                this.lastCity = this.city
                this.getHomeInfo()
            }
        }
    }
</script>
<style>

</style>
