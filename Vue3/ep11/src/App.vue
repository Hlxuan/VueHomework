<template>
  <div>
    <h2>新股价：{{ newPrice }}</h2>
    <h2>旧股价：{{ oldPrice }}</h2>
    <h2 :style="myStyle">
      <span v-if="differentPrice >= 0">涨</span><span v-else>跌</span>：{{
        differentPrice
      }}
    </h2>
    <button @click="Switch">
      <span v-if="timer == null">开启</span>
      <span v-else>关闭</span>
    </button>
  </div>
</template>

<script>
import { ref, onMounted, watch } from "vue";

export default {
  name: "App",
  setup() {
    let newPrice = ref(0);
    let oldPrice = ref(0);
    let differentPrice = ref(0);
    let myStyle = {
      color: "black",
    };
    let timer = ref(null);

    onMounted(() => {
      change();
    });

    watch(newPrice, (newValue, oldValue) => {
      oldPrice.value = oldValue;
      differentPrice.value = newValue - oldValue;
      if (differentPrice.value > 0) {
        myStyle.color = "red";
      } else if (differentPrice.value < 0) {
        myStyle.color = "green";
      } else {
        myStyle.color = "black";
      }
    });

    function change() {
      timer.value = setInterval(() => {
        newPrice.value = Math.floor(Math.random() * 101);
      }, 1000);
    }

    function Switch() {
      if (timer.value === null) {
        change();
      } else {
        clearInterval(timer.value);
        timer.value = null;
      }
    }

    return {
      newPrice,
      timer,
      oldPrice,
      differentPrice,
      myStyle,
      Switch,
    };
  },
};
</script>

<style>
</style>
