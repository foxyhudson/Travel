<template>
    <div>
      <div class="title">热销推荐</div>
      <ul>
        <li class="item border-bottom" v-for="(item,index) of recommendList" :key="item.id">
          <img class="item-img"  :src="item.imgUrl" alt="">
          <div class="item-info">
            <p class="item-title">{{item.title}}</p>
            <p class="item-desc">{{item.desc}}</p>
            <button class="item-button">查看详情</button>
          </div>
        </li>
      </ul>
    </div>
</template>

<script>
    export default {
        name: "HomeRecommend",
        props:{
          recommendList:Array
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
    margin-top: .2rem
    padding-left: .2rem
    line-height: .8rem
    background: #eee
    text-align: .2rem
  .item
    display: flex
    overflow: hidden
    height: 1.9rem

    .item-img
      width:1.7rem
      height: 1.7rem
      padding: .1rem
    .item-info
      flex:1
      padding: .1rem
      min-width: 0
      .item-title
        line-height: .54rem
        font-size: .32rem
        ellipsis()
      .item-desc
        height: .4rem
        line-height: .4rem
        color: #ccc
        ellipsis()
      .item-button
        line-height: .44rem
        background: #ff9300
        padding: 0 .2rem
        border-radius: .06rem
        margin-top: .16rem
        color: #fff
</style>
