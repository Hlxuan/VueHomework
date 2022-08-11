<template>
  <div>
    <button>btn1</button>
    <button>btn2</button>
    <button>btn3</button>
    <button>btn4</button>
    <button>btn5</button>
  </div>
</template>

<script>
import { onMounted } from "vue";
export default {
  name: "App",
  setup() {
    onMounted(() => {
      button();
    });

    function button() {
      let btn = document.getElementsByTagName("button");
      for (let i = 0; i < btn.length; i++) {
        btn[i].addEventListener("click", () => {
          console.log(btn[i].innerHTML);
        });
      }
    }

    return {
      
    };
  },
};
</script>

