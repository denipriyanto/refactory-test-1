<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <div class="sorting-app">
      <h1>Sorting APP</h1>
      <input type="number" placeholder="number input" v-model="inputan">
      <button v-on:click="sorting()">Sorting</button>
      <br>
      <h3>{{inputan}}</h3>
      <div class="action">
      </div>

      <ul>
        <li v-for="log in loging" v-bind:key="log._id">
          {{log}}
        </li>
      </ul>
      <p v-if="input.length">Jumlah swap = <b>{{swaplength}}</b></p>
    </div>
  </div>
</template>

<script>

export default {
  name: 'app',
  data : ()=>{
    return {
      inputan : '',
      input : [],
      swaplength : 0,
      loging : []
    }
  },
  methods : {
    sorting(){
      var self = this;
      // this.reset();
      for (var i = 0; i < self.inputan.length; i++){
        self.input.push(self.inputan[i]);
      }
      this.sorted();
    },
    sorted(){
      var length = this.input.length;
      let input = this.input;

      for (var i=0; i < length; i++){
        for(var j=0; j < length-1-i; j++){
          if(input[j+1] < input[j]){
            this.swap(input, j, j+1);
            this.log(input[j], input[j+1], input );
          }
        }
      }
    },
    swap(array, index1, index2){
      var aux = array[index1];
      array[index1] = array[index2];
      array[index2] = aux;
      this.swaplength++;
    },
    log(index1, index2, array){
      let logString = '['+index1+','+index2+'] -> '+array.toString();
      this.loging.push(logString);
    },
    reset(){
      this.inputan = '';
      this.input = [];
      this.swaplength = 0;
      this.loging = [];
    }
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
}

#app {
  position: relative;
  height: 100vh;
}

body {
  margin: 0;
}

.sorting-app {
  width: 300px;
  min-height: 420px;
  border: 1px solid #ccc;
  position: absolute;
  top:0;
  left: 50%;
  transform: translate(-50%, 20%);
  padding: 0 20px;
  border-radius: 4px;
}


input, button {
  padding: 8px 20px;
}

button {
  margin-left: 15px;
}

ul {
  list-style-type: none;
  margin: 0;
  padding: 0;
}
ul li {
  padding: 8px 0;
}
b {
  margin-top: 20px;
}
</style>
