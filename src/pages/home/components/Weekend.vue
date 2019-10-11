<template>
    <div>
      <div class="title">周末去哪儿</div>
      <ul>
        <li class="item border-bottom" v-for="(item,index) of weekendList" :key="item.id">
          <div class="item-img-wrapper">
            <img class="item-img"  :src="item.imgUrl" alt="">
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
        name: "HomeWeekend",
        props:{
          weekendList:Array
        },
        data(){
          return{
          }
        }
    }
</script>

<style scoped lang="stylus">
  @import "~styles/mixins.styl"
  .title

    padding-left: .2rem
    line-height: .8rem
    background: #eee
    text-align: .2rem
  .item-img-wrapper
    padding-bottom: 37.09%
    overflow: hidden
    height: 0
    .item-img
      width: 100%
  .item-info
      padding: .1rem
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
      .item-desc
        height: .4rem
        line-height: .4rem
        color: #333
        ellipsis()

</style>
