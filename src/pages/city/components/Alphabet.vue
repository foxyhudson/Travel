<template>
      <ul class="list">
        <li class="item" v-for="item of letters"  :key="item"
            :ref="item"
          @click="handleLetterClick"
          @touchstart.prevent="handleTouchStart"
          @touchmove="handleTouchMove"
          @touchend="handleTouchEnd"
        >{{item}}</li>
      </ul>
</template>

<script>
    export default {
        name: "CityAlphabet",
        props:{
          cities:Object
        },
        data(){
          return{
            touchStatus:false,
            startY:0, //不用每次滑动的时候去算位置 因为这个位置时固定的
            time: null//节流用
          }
        },
        updated(){  //当页面数据更新触发 也没面加载时 City 的cities:{},其实空 当ajax返回数据后触发updated
          this.startY = this.$refs['A'][0].offsetTop
        },
        computed:{
          letters(){
            const letters = [];
            for(let i in this.cities){
              letters.push(i)
            }
            return letters
          }
        },
        methods:{
          handleLetterClick(e){
            this.$emit('change',e.target.innerText)
          },
          handleTouchStart(){
            this.touchStatus = true
          },
          handleTouchMove(e){
            if(this.touchStatus){
              if(this.timer){
                clearTimeout(this.time)
              }
              this.timer = setTimeout(()=>{ //节流 延迟16毫秒后执行 降低move频率提高性能
                const touchY = e.touches[0].clientY - 79//e.touches[0]事件对象获取到手指所在位置信息 需要减去上面绿色 高度
                console.log(touchY)
                const index = Math.floor((touchY - this.startY) / 20) //20是每个字母的高度 通过这样能知道是第几个字母
                console.log(index)
                if(index >= 0 && index < this.letters.length){
                  this.$emit('change',this.letters[index])
                }
              },16)
            }
          },
          handleTouchEnd(){
            this.touchStatus = false
          }
        }
    }
</script>

<style lang="stylus" scoped>
  @import "~styles/varibles.styl"
  .list
    display: flex
    flex-direction : column  //垂直居中
    justify-content: center     //垂直居中
    position: absolute;
    right: 0
    top: 1.58rem
    bottom: 0
    width: .4rem
    .item
      text-align: center //水平居中
      line-height: .4rem
      color: $bgColor

</style>
