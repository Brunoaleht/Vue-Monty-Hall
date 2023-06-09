<template>
  <div class="gift">
    <div class="giftTie1"></div>
    <div class="giftTie2"></div>
    <div class="giftLid"></div>
    <div class="giftBox"></div>
  </div>
</template>

<script>
export default {
  name: "GiftBox",
};
</script>

<style>
.gift {
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  z-index: 10px;
}
.giftLid {
  width: 100px;
  height: 20px;
  background-color: rgb(99, 99, 197);
}
.giftBox {
  width: 90px;
  height: 60px;
  background-color: rgb(54, 54, 112);
}
.giftTie1 {
  position: absolute;
  width: 15px;
  height: 80px;
  background-color: red;
}
.giftTie2 {
  position: absolute;
  top: 35px;
  width: 90px;
  height: 15px;
  background-color: red;
}
</style>
