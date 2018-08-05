<template>
    <div>
        <city-header></city-header>
        <city-search :ct="cities"></city-search>
        <city-list :ct="cities" :hct="hotCities" :letter="letter"></city-list>
        <city-alphabet :ct="cities" @change="handleChange"></city-alphabet>
    </div>
</template>
<script>
    import CityHeader from './components/Header'
    import CitySearch from './components/Search'
    import CityList from './components/List'
    import CityAlphabet from './components/Alphabet'
    import axios from 'axios'

    export default{
        data(){
            return {
                cities:{},
                hotCities:[],
                letter:''
            }
        },
        components:{
            CityHeader,
            CitySearch,
            CityList,
            CityAlphabet
        },
        mounted(){
            this.getCityInfo()
        },
        methods:{
            getCityInfo(){
                axios.get('api/city.json')
                .then(this.getCityInfoSucc)
            },
            getCityInfoSucc(res){
                console.log(res);
                res = res.data;
                if(res.ret && res.data){
                    const data = res.data
                    this.cities = data.cities
                    this.hotCities = data.hotCities
                }
            },
            handleChange(letter){
                this.letter = letter;
            }
        }
    }
</script>
<style lang="stylus" scoped>

</style>
