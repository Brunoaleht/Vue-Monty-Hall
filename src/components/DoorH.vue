<template>
  <div>
    <div class="doorArea">
      <div class="doorFrame" :class="{ selected: selected && !open }">
        <GiftBox v-if="open && hasGift" />
      </div>
      <div class="door" :class="{ open }" @click="selectPort">
        <div class="number" :class="{ selected }">{{ number }}</div>
        <div class="knob" :class="{ selected }" @click.stop="open = true"></div>
      </div>
    </div>
  </div>
</template>

<script>
import GiftBox from "./GiftBox.vue";
export default {
  name: "DoorH",
  components: {
    GiftBox,
  },
  props: {
    number: {},
    hasGift: { type: Boolean },
  },
  data: function () {
    return {
      open: false,
      selected: false,
    };
  },
  methods: {
    selectPort() {
      this.$emit("portSelected", this.number);
    },
  },
};
</script>

<style>
:root {
  --door-border: 5px solid brown;
  --selected-border: 5px solid yellow;
}
.doorArea {
  position: relative;
  width: 200px;
  height: 310px;
  border-bottom: 10px solid #aaa;
  margin-bottom: 20px;
  font-size: 3rem;

  display: flex;
  justify-content: center;
}
.doorFrame {
  position: absolute;
  height: 300px;
  width: 180px;

  border-left: var(--door-border);
  border-top: var(--door-border);
  border-right: var(--door-border);

  display: flex;
  justify-content: center;
  align-items: flex-end;
}
.door {
  position: absolute;
  top: 5px;
  height: 295px;
  width: 170px;
  background-color: chocolate;

  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 15px;
}
.door .knob {
  width: 20px;
  height: 20px;
  border-radius: 10px;
  background-color: brown;
  align-self: flex-end;
  margin-top: 60px;
}
.doorFrame.selected {
  border-left: var(--selected-border);
  border-top: var(--selected-border);
  border-right: var(--selected-border);
}
.door .number.selected {
  color: yellow;
}
.door .knob.selected {
  background-color: yellow;
}
.door.open {
  background-color: #0007;
}
.door.open .number {
  display: none;
}
.door.open .knob {
  display: none;
}
</style>
