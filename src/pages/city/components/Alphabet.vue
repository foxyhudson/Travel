<template>
      <ul class="list">
        <li class="item" v-for="(item,key) of cities"  :key="key">{{key}}</li>
      </ul>
</template>

<script>
    export default {
        name: "CityAlphabet",
        props:{
          cities:Object
        }
    }
</script>
f
<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .list
    display: flex
    flex-direction : column  //垂直居中
    justify-content: center     //垂直居中
    position: absolute;
    right: 0
    top :0
    bottom: 0
    width: .4rem
    .item
      text-align: center //水平居中
      line-height: .4rem
      color: $bgColor

</style>
