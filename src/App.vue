<template>
  <div id="app">
    
    <div class="test" :style="blockColor">
    
    </div>
    <div>
      <input type="range" min="0" max="255" value="0" v-model="red">
        <label for="">
          RED
        </label>
    </div>
    <div>
      <input type="range" min="0" max="255" value="0" v-model="green"> 
        <label for="">
          GREEN
        </label>
    </div>
    <div>
      <input type="range" min="0" max="255" value="0" v-model="blue">
        <label for="">
          BLUE
        </label>
    </div>
    
  </div>
</template>

<script>

export default {
  name: 'app',
  data() {
    return {
      red: null,
      green: null,
      blue: null,
      blockColor:{
        backgroundColor: rgbGen(red, green, blue)
      }
    }
  },
  methods:{
    rgbGen (red, green, blue){
      return `rgb(${red}, ${green}, ${blue})`;
    }
  }
}
</script>

<style scoped>
  .test{
      width:100px;
      height: 100px;
  }
</style>
