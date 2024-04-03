<template>
  <div class="grid">
    <input v-model="title" type="text" placeholder="0" />
    <button
      class="cell num"
      v-for="num in numbers"
      :key="num"
      @click="addInput(num)"
    >
      {{ num }}
    </button>
    <button
      class="cell op"
      v-for="op in operations"
      :key="op"
      @click="addInput(op)"
    >
      {{ op }}
    </button>
    <button class="cell op" @click="clearInput">R</button>
    <button class="cell op" @click="result">=</button>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      title: "",
      str: "",
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0],
      operations: ["+", "-", "*", "/"],
    };
  },

  methods: {
    addInput(char) {
      this.title = this.str += char;
      console.log(this.str);
    },

    result() {
      this.title = eval(this.str);
    },

    clearInput() {
      this.title = "";
      this.str = "";
    },
  },
};
</script>

<style>
* {
  font-family: "Gilroy", sans-serif;
  transition: 0.3s all;
  font-weight: 600;
}
#app {
  width: 200px;
  box-shadow: 0 3px 15px grey;
}
input[type="text"] {
  width: 200px;
  border: 0;
  color: #243849;
  font-size: 18px;
  padding: 5px 5px;
  text-align: right;
}
.grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  width: 100%;
}
.cell {
  flex: 33%;
  height: 50px;
  font-size: 18px;
  border: none;
}
.num {
  background-color: #243849;
  color: #fff;
  font-weight: 400;
}
.cell:hover {
  background-color: #182530;
}
.op {
  background-color: #ff9900;
  color: #243849;
}
</style>
