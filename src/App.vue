<template>
  <div id="app">
    <h1>Problema de MontyHall</h1>
    <div class="form">
      <div v-if="!started">
        <label for="portsAmount">How many doors? </label>
        <input
          type="text"
          id="portsAmount"
          size="3"
          v-model.number="portsAmount"
        />
      </div>
      <div v-if="!started">
        <label for="giftedPort">What is the chosen port? </label>
        <input
          type="text"
          id="giftedPort"
          size="3"
          v-model.number="giftedPort"
        />
      </div>
      <button v-if="!started" @click="started = true">Start</button>
      <button v-if="started" @click="started = false">Re-Start</button>
    </div>
    <div class="doors" v-if="started">
      <div v-for="i in portsAmount" :key="i">
        <DoorH
          :hasGift="i === giftedPort"
          :number="i"
          @portSelected="portSelected"
          :selected="selectedPort == i"
        />
      </div>
    </div>
  </div>
</template>

<script>
import DoorH from "./components/DoorH.vue";

export default {
  name: "App",
  components: { DoorH },
  data: function () {
    return {
      started: false,
      portsAmount: 5,
      giftedPort: null,
      selectedPort: null,
    };
  },
  methods: {
    portSelected(selectedPort) {
      this.selectedPort = selectedPort;
    },
  },
};
</script>

<style>
* {
  font-family: "Montserrat", sans-serif;
  box-sizing: border-box;
}
body {
  color: #fff;
  background: linear-gradient(to right, #08aeea 0%, #2af598 100%);
}
#app {
  display: flex;
  flex-direction: column;
  align-items: center;
}
#app h1 {
  border: solid 1px #000;
  background-color: #0006;
  padding: 20px;
  margin-bottom: 60px;
}
.form {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  margin-bottom: 40px;
}
.form,
.form input,
.form button {
  margin-bottom: 10px;
  font-size: 2rem;
}
.doors {
  align-self: stretch;
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap;
}
</style>
