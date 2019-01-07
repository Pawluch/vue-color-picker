<template>
  <div id="app">
    
    <div class="test" :style="{backgroundColor: rgbGen(red, green, blue)}">
    
    </div>
    <div>
      <input type="range" min="0" max="255" v-model="red">
        <label for="red_text">
          RED
        </label>
    </div>
    <div>
      <input type="range" min="0" max="255" v-model="green"> 
        <label for="">
          GREEN
        </label>
    </div>
    <div>
      <input type="range" min="0" max="255" v-model="blue">
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
      red: 0,
      green: 0,
      blue: 0
    }
  },
  methods:{
    rgbGen: function(red, green, blue){
      return `rgb(${red}, ${green}, ${blue})`;
    }
  }
}
</script>

<style scoped>
  .test{
      width: 100px;
      height: 100px;
      background-color: green;
  }
</style>
