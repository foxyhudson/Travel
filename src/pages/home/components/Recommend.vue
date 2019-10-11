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
        data(){
          return{
            recommendList:[{
              id:'0001',
              imgUrl:"http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_250x250_0fc722c0.jpg",
              title:"北京世界园艺博览会",
              desc:"导游 柳青玲 的讲解非常棒！声音洪亮，思路清晰！体验很好，一场爱国主义教育"},
              {
                id:'0002',
                imgUrl:"http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_250x250_0fc722c0.jpg",
                title:"北京世界园艺博览会",
                desc:"导游 柳青玲 的讲解非常棒！声音洪亮，思路清晰！体验很好，一场爱国主义教育"},
              {
                id:'0003',
                imgUrl:"http://img1.qunarzz.com/sight/p0/1409/19/adca619faaab0898245dc4ec482b5722.jpg_250x250_0fc722c0.jpg",
                title:"北京世界园艺博览会",
                desc:"导游 柳青玲 的讲解非常棒！声音洪亮，思路清晰！体验很好，一场爱国主义教育"},
              ]
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
