<template>
  <div id="app">
    <h1>What Are The Odds?</h1>
    <form action="" v-on:click.prevent="">
      <h2>
        Odds are between 1 and
        <input v-model="topNumber" type="number" min="1" />
      </h2>
      <button id="roll" v-show="topNumber" v-on:click.prevent="roll()">
        <img src="./assets/dice.png" alt="" /> Roll That Shit!
      </button>
    </form>

    <p class="result" v-show="firstNumber">
      <span class="first">{{ firstNumber }}</span> /
      <span class="second">{{ secondNumber }}</span>
    </p>

    <p class="reload" v-show="firstNumber">
      Roll Again?
      <button v-on:click.prevent="reload()">
        <img src="./assets/redo-alt.svg" alt="" /> Refresh
      </button>
    </p>

    <p v-show="matches" class="matches">Numbers Match!</p>
    <img v-show="matches" src="./assets/ohshit.gif" alt="" />
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      topNumber: "",
      firstNumber: "",
      secondNumber: "",
      matches: false
    };
  },
  methods: {
    roll: function() {
      document.querySelector("#roll").style.display = "none";
      var top = this.topNumber;
      var interval = setInterval(function() {
        $("#number").text(number);
        if (number >= target) clearInterval(interval);
        number++;
      }, 30);
      for (var i = 0; i < top; i++) {}
      this.firstNumber = Math.floor(Math.random() * top + 1);
      this.secondNumber = Math.floor(Math.random() * top + 1);

      document.querySelector(".first").style.opacity = 1;
      document.querySelector(".second").style.opacity = 1;
      document.querySelector(".first").style.transform = "none";
      document.querySelector(".second").style.transform = "none";

      if (this.firstNumber == this.secondNumber) {
        this.matches = true;
        document.querySelector(".first").style.color = "red";
        document.querySelector(".first").style.fontWeight = "bold";
        document.querySelector(".second").style.color = "red";
        document.querySelector(".second").style.fontWeight = "bold";
      }
    },
    reload: function() {
      location.reload();
    }
  }
};
</script>

<style lang="scss">
body {
  margin: 0;
  padding: 0;
  background: #f9f9f9;
  font-size: 18px;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

h1 {
  font-size: 72px;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}

form {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
}

input[type="number"] {
  background: transparent;
  border: none;
  border-width: 0 0 2px 0;
  border-style: solid;
  text-align: center;
  font-size: 1em;
  width: auto;
  display: inline;
  max-width: 90px;
}

button {
  align-items: center;
  background-color: #fff;
  border-radius: 8px;
  border: 2px solid #e0e0e0;
  color: #2c3e50;
  cursor: pointer;
  display: flex;
  font-size: 18px;
  justify-content: space-around;
  min-height: 48px;
  padding: 1rem 2rem;
  transition: background-color 0.3s;

  img {
    max-width: 30px;
    margin-right: 1rem;
  }

  &:hover {
    background-color: #e4e4e4;
  }
}
.result {
  font-size: 40px;
}
.first,
.second {
  opacity: 0;
  transform: translateY(-2rem);
  transition: transform 0.5s, opacity 0.5s;
  transition-delay: 1s;
}
.first {
  color: blue;
}
.second {
  color: green;
}
.matches {
  font-size: 72px;
  color: red;
}
.reload {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;

  button {
    margin-top: 1rem;
  }
}
</style>
