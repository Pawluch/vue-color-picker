<template>
  <div id="app">
    <div class="container">
      <div class="test" :style="{backgroundColor: rgbGen(red, green, blue) || hex_color}">
    
      </div>

      <div class="color_input">
        <input type="range" min="0" max="255" v-model="red">
        <label for="red_text">
          RED
        </label>
        <input type="number" id="red_text" min="0" max="255" required v-model="red">
      </div>
      <div class="color_input">
        <input type="range" min="0" max="255" v-model="green"> 
        <label for="green_text">
          GREEN
        </label>
        <input type="number" id="green_text" min="0" max="255" required v-model="green">
      </div>
      <div class="color_input">
        <input type="range" min="0" max="255" v-model="blue">
        <label for="blue_text">
          BLUE
        </label>
        <input type="number" id="blue_text" min="0" max="255" required v-model="blue">
      </div>
      <div class="copy_output">
        <label for="">Your color: </label>
        <input type="text" v-model="hex_color" class="copy_text" >
        {{rgbToHex(red, green, blue)}}
        <button @click="copyText()" >COPY</button>
      </div>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data() {
    return {
      red: Math.floor(Math.random()*255),
      green: Math.floor(Math.random()*255),
      blue: Math.floor(Math.random()*255),
      hex_color: ``
    }
  },
  methods:{
    rgbGen: function(red, green, blue){
      return `rgb(${red}, ${green}, ${blue})`;
    },

    rgbToHex: function(red, green, blue){
      let colorArr = [red || 0, green || 0, blue || 0];
      
      let colorString = colorArr.map(n => n < 256 ? parseInt(n).toString(16) : '255')
                                .map(n => n.length < 2 ? '0' + n : n)
                                .join('')

      this.$data.hex_color = `#${colorString}`;
    },

    copyText: function(){
      let copiedText = document.querySelector('.copy_text');
      copiedText.select();
      document.execCommand('copy');
    }

  }
}
</script>

<style scoped>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  #app{
    height: 100vh;
    background-color: #666;
    font-family: 'Lucida Sans', sans-serif;
  }
  
  .container{
    border: 1px black solid;
    max-width: 295px;
    padding: 30px 0;
    margin: 0 auto;
    transform: translateY(15vh);
    background-color: white;
  }

  .test{
      width: 200px;
      height: 100px;
      margin: 0 auto 20px auto;
  }

  .color_input{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .color_input > *{
    margin: 10px 10px;
  }

  .color_input input[type=range]{
    width: 100px;
  }

  .color_input label{
    width: 60px;
  }

  .color_input input[type=number]{
    width:55px;

  }

  .copy_output{
    display: flex;
    justify-content: center;
    align-items: center;
  }

  .copy_output *{
    margin: 10px 5px;
  }

  .copy_output input {
    width: 70px;
    text-align: center;
  }
</style>
