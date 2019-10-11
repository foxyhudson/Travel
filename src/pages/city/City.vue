<template>
    <div>
      <city-header></city-header>
      <city-search></city-search>
      <city-list :hotCities="hotCities" :cities="cities" :letter="letter"></city-list>
      <city-alphabet @change="handleLetterChange" :cities="cities"></city-alphabet>
    </div>
</template>

<script>
    import CityHeader from "./components/Header"
    import CitySearch from "./components/Search"
    import CityList from "./components/List"
    import CityAlphabet from "./components/Alphabet"
    import axios from 'axios'
    export default {
        name: "City",
        components:{
          CityHeader,
          CitySearch,
          CityList,
          CityAlphabet
        },
        data(){
          return{
            hotCities:[],
            cities:{},
            letter:""
          }
        },
        mounted() {
          this.getListInfo()
        },
        methods:{
          getListInfo(){
            axios.get('/api/city.json')
              .then(this.getListInfoSucc)
          },
          getListInfoSucc(res){
            res = res.data
            if(res.ret && res.data){
              const data = res.data
              this.hotCities = data.hotCities
              this.cities = data.cities
            }
          },
          handleLetterChange(letter){
            this.letter = letter
          }
        }
    }
</script>

<style scoped lang="stylus">

</style>
