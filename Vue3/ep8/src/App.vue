<template>
  <div>
    <button @click="myClass.darkMode = !myClass.darkMode">暗黑模式</button>
    <button @click="myClass.border = !myClass.border">边框模式</button>
    <button @click="fontNum++">字体放大</button>
    <button @click="fontNum--">字体缩小</button>
    <p :class="myClass" :style="myStyle">
      操作元素的 class 列表和内联样式是数据绑定的一个常见需求。因为它们都是
      attribute，所以我们可以用 v-bind
      处理它们：只需要通过表达式计算出字符串结果即可。不过，字符串拼接麻烦且易错。因此，在将
      v-bind 用于 class 和 style 时，Vue.js
      做了专门的增强。表达式结果的类型除了字符串之外，还可以是对象或数组.
    </p>
  </div>
</template>

<script>
import { ref, reactive, computed } from "vue";

export default {
  name: "App",

  setup() {
    let myClass = reactive({
      darkMode: false,
      border: false,
    });

    let fontNum = ref(15);

    let myStyle = computed(() => {
      return {
        fontSize: fontNum.value + "px",
      };
    });

    return {
      myClass,
      fontNum,
      myStyle,
    };
  },
};
</script>

<style>
  p {
    text-align: justify;
  }
  .darkMode {
    background-color: #1b1b1b;
    color: white;
  }
  .border {
    border: 1px solid black;
  }
</style>