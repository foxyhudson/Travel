<template>
    <div>
      <div class="title">周末去哪儿</div>
      <ul>
        <li class="item border-bottom" v-for="(item,index) of recommendList" :key="item.id">
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
        data(){
          return{
            recommendList:[{
              id:'0001',
              imgUrl:"http://img1.qunarzz.com/sight/source/1509/81/0412da9c4db66a.jpg_r_640x214_8e23871e.jpg",
              title:"帝都必打卡",
              desc:"来北京必去的景点非这些地方莫属"},
              {
                id:'0002',
                imgUrl:"http://img1.qunarzz.com/sight/source/1505/9e/21df651e19af5d.jpg_r_640x214_3ea5bb38.jpg",
                title:"登高望远秋色佳",
                desc:"山顶满眼彩色，此情此景醉了"},
              {
                id:'0003',
                imgUrl:"http://img1.qunarzz.com/sight/source/1505/aa/7baaf8a851d221.jpg_r_640x214_1431200f.jpg",
                title:"寻找北京的皇城范儿",
                desc:"数百年的宫廷庙宇，至今依旧威严霸气"},
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
  .item-img-wrapper
    padding-bottom: 33.9%
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
