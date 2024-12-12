<template>
    <div id="app">
         <ReuseableBtn name="Login"/>      
  </div>
</template>

<script>
import ReuseableBtn from './components/ReuseableBtn.vue';
export default {
  name: 'App',
  components: {
    ReuseableBtn
  },
  data(){
    return{

    }
  },
 
}
</script>

<style scoped>
#app{
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100vh;
}
</style>
