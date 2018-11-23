<template>
  <div id="app">
    <!-- <div v-for="item in items" :key="item.id">
      <img :src="item.img">
    </div> -->
    <transition-group tag="ul" class="wrap" name="image">
      <li v-for="item in items" :key="item.id" v-show="item.id === index">
        <img :src="item.img">
      </li>
    </transition-group>
  </div>
</template>

<script>
export default {
  name: 'App',
  data(){
    return{
      items: [
        { id:1, img:'/static/jiazhiguan.jpg'},
        { id:2, img:'/static/cangshu.jpg'},
        { id:3, img:'/static/gugugu.jpg'},
        { id:4, img:'/static/ningmeng.jpg'}
      ],
      index: 1      
    }
  },
  methods: {
    play(){
      setInterval(this.autoplay, 3000)
    },
    autoplay(){
      this.index++;
      if(this.index === 5){
        this.index = 1
      }
    },

  },
  created(){
    this.play()
  }
  
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}


li{
  position: absolute;
}

.image-enter-active{
  transform: translateX(0);
  transition: all 1.5s ease;
}
.image-leave-active{
  transform: translateX(-100%);

  transition: all 1.5s ease;
}
.image-leave{
  opacity: 0;
}
.image-enter{
  transform: translateX(100%)
}
.image-leave-to{
  transform: translateX(0)
}

</style>
