<template>
  <div class="home">
    <n-grid :cols="3">
      <n-gi>
        <div class="light-green"></div>
      </n-gi>
      <n-gi>
        <div class="green"></div>
      </n-gi>
      <n-gi>
        <div class="light-green"></div>
      </n-gi>
      <n-gi>
        <div class="green"></div>
      </n-gi>
      <n-gi>
        <div class="light-green"></div>
      </n-gi>
      <n-gi>
        <div class="green"></div>
      </n-gi>
      <n-gi>
        <div class="light-green"></div>
      </n-gi>
      <n-gi>
        <div class="green">
          距2022还有{{date}}
        </div>
      </n-gi>
      <n-gi>
        <div class="light-green"></div>
      </n-gi>
      <n-gi>
        <div class="green"></div>
      </n-gi>
      <n-gi>
        <div class="light-green"></div>
      </n-gi>
      <n-gi>
        <div class="green"></div>
      </n-gi>
    </n-grid>
  </div>
</template>

<script>
import { onUnmounted, ref } from '@vue/runtime-core'
export default {
  name: 'Home',
  components: {
  },
  setup(){
    var date = ref('');
    const changeText=()=>{
        var date1 = new Date() ;
        var date2 = Date.parse(new Date("2022/1/1"));
        var day = parseInt((date2-date1)/ (1000 * 60 * 60 * 24)) - 1;
        var hours = parseInt(((date2-date1) % (1000 * 60 * 60 * 24))/(1000*60*60));
        var minutes = parseInt((((date2-date1) % (1000 * 60 * 60 * 24)) % (1000*60*60))/(1000 * 60));
        var seconds = parseInt(((((date2-date1) % (1000 * 60 * 60 * 24)) % (1000*60*60))%(1000 * 60))/1000);
        date.value=day+" : "+hours+ " : "+minutes + " : "+seconds;
    }
    var countDown=setInterval(()=>changeText(),1000);
    onUnmounted(()=>{
      clearInterval(countDown);
      console.log("定时器停止");
    })
    
    return{
      countDown,
      date,
      changeText
    }
  },
  
}
</script>
<style scoped>
.home{
  height:100vh;
  background: url('../assets/switzerland.gif') no-repeat;
  background-size: 100% 100%;
}
.light-green {
  height: 108px;
  /* background-color: rgba(0, 128, 0, 0.12); */
}
.green {
  height: 108px;
  font-size: 50px;
  color: white;
  font-family: 'Segoe UI', Helvetica, Arial, sans-serif;
  /* background-color: rgba(0, 128, 0, 0.24); */
}
</style>
