<template>
  <div class="wrapper" ref="wrapper">
      <div class="content" ref="content">
        <ul>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
          <li>呃呃呃</li>
        </ul>
    </div>
    <div class="yuan" id="yuan">
      显示更多
    </div>
</div>
</template>

<script>
import BScroll from 'better-scroll'

export default {
  name: 'hello',
  mounted() {
      this.$nextTick(() => {
        this.$refs.content.style.width = '1800px';
        //$refs绑定元素
        if(!this.scroll){
            this.scroll = new BScroll(this.$refs.wrapper, {
              //开启点击事件 默认为false
              click:true,
              scrollX: true,
              scrollY: false,
              eventPassthrough:'vertical',
              probeType:3,//监听scroll
            })
            this.scroll.on('scroll', (pos) => {
              console.log(-pos.x - 1298)
              document.getElementById('yuan').style.right = -pos.x - 1298 - 260 +'px'
            })
        }else if(!this.$refs.wrapper){
            return
        }
        else{
            this.scroll.refresh()
        }
      })
  }
}
</script>

<style scoped>
  .wrapper{
  width: 500px;
  position: relative;
  top: 20px;
  left: 100px;
  /* bottom: 50px;  关键 */
  overflow: hidden;
  height: 100px;
  z-index: 1;
  border: 1px red solid;
}
ul{
  display: -webkit-box;
  list-style: none;
  padding: 0;
}
li{
  width: 100px;
}
.yuan{
  position: absolute;
  padding-left: 40px;
  padding-right: 200px;
  background-color: #fbb111;
  width: 20px;
  font-size: 12px;
  line-height: 15px;
  color: #ffffff;
  height: 60px;
  border-radius: 30px 0 0 30px;
  top: 0;
  right: -260px;
}
</style>
