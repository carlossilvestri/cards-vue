<template>
  <div id="app">
    <main>
      <div class="buttons-container">
        <button class="button-style" type="button" @click="getRandomNumber()">Random Cards</button>
        <button class="button-style" type="button" @click="onReset()">
          Reset Cards
        </button>
      </div>
      <div class="cards-container">
        <div class="card" v-for="(a, index) in data1" v-bind:key="index">
          <div class="number-card-left">
            {{ a.number }}
            <p :class="{ red: a.isRed }">{{ a.icon }}</p>
          </div>
          <p class="t-center" :class="{ red: a.isRed }">{{ a.icon }}</p>
          <div class="number-card-right">
            {{ a.number }}
            <p :class="{ red: a.isRed }">{{ a.icon }}</p>
          </div>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
export default {
  name: "App",
  components: {},
  data() {
    return {
      icons: ["❤", "♦", "♣️", "♠"],
      data1: [
        {
          icon: "❤",
          number: 1,
          isRed: true
        },
        {
          icon: "♦",
          number: 2,
          isRed: false
        },
        {
          icon: "♣️",
          number: 3,
          isRed: false
        },
        {
          icon: "♠",
          number: 4,
          isRed: false
        },
      ],
      data2: [
        {
          icon: "❤",
          number: 1,
          isRed: true
        },
        {
          icon: "♦",
          number: 2,
          isRed: false
        },
        {
          icon: "♣️",
          number: 3,
          isRed: false
        },
        {
          icon: "♠",
          number: 4,
          isRed: false
        },
      ],
    };
  },
  methods: {
    getRandomNumber() {
      let a = [];
      for (let i = 0; i < 4; i++) {
        a.push({
          icon: this.icons[ Math.floor(Math.random() * 3)],
          number: Math.ceil(Math.random() * 20),
          isRed: (Math.random() < 0.5)
        });
      }
      this.data1 = a;
    },
    onReset() {
      this.data1 = JSON.parse(JSON.stringify(this.data2));
    },
  },
};
</script>

<style lang="scss">
// Variables
$main-color: #2a96f0;
$main-font: "Poppins", "Source Sans Pro", -apple-system, BlinkMacSystemFont,
  "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif;

.buttons-container {
  display: flex;
  justify-content: center;
  align-items: center;
  font-family: $main-font;
  .button-style {
    background: $main-color;
    border: 1px solid $main-color;
    box-sizing: border-box;
    box-shadow: 3px 4px 4px rgba(0, 0, 0, 0.25);
    border-radius: 47px;
    color: white;
    padding: 8px 15px;
    transition: all 0.5s;
    margin-top: 10px;
    margin-left: 10px;
    &:hover {
      cursor: pointer;
      color: $main-color;
      background-color: white;
    }
  }
}
.cards-container {
  display: flex;
  margin-top: 10px;
  width: 100%;
  font-family: $main-font;
  @media (max-width: 720px) {
    flex-direction: column;
    justify-content: center;
    align-items: center;
    margin-top: 20px;
  }
  .card {
    border: 1px solid black;
    -webkit-box-shadow: 4px 0px 10px 1px rgba(0, 0, 0, 0.73);
    box-shadow: 4px 0px 10px 1px rgba(0, 0, 0, 0.73);
    height: 300px;
    width: 200px;
    margin-left: 10px;
    display: flex;
    flex-direction: column;
    justify-content: space-between;
    border-radius: 5px;
    @media (max-width: 720px) {
      margin-top: 20px;
    }
    .number-card-left {
      margin: 10px 0 5px 10px;
      display: flex;
      flex-direction: column;
      justify-content: flex-start;
      align-items: flex-start;
      p {
        margin: 0;
      }
    }
    .number-card-right {
      margin: 10px 0 5px 10px;
      display: flex;
      flex-direction: column;
      justify-content: flex-end;
      align-items: flex-end;
      margin: 0 10px 0 0;
      p {
        margin: 0;
      }
    }
  }
}
/* Utilidades */
.t-center {
  text-align: center;
  font-size: 30px;
}
.red {
  color: red;
}
.black {
  color: black;
}
</style>
