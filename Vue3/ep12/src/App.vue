<template>
  <div>
    <myPeople :job="Tjobs" :number="Tnumber">
      <button @click="set">{{ btnText }}</button>
    </myPeople>
    <hr />
    <myPeople :job="Sjobs" :number="Snumber">
      <img
        src="https://www.gkd.edu.cn/upload/images/2022/3/189e568bed4b5bdf.jpg"
        alt="广科大学生图片"
      />
    </myPeople>
  </div>
</template>

<script>
import myPeople from "./components/myPeople.vue";
import {ref} from "vue";

export default {
  name: "App",
  setup() {
    let Tjobs = ref("Teacher");
    let Sjobs = ref("Student");
    let Tnumber = ref(1);
    let Snumber = ref(10);
    let timer = null;
    let btnText = ref("ON");

    function set(){
      if(timer){
        clearInterval(timer);
        btnText.value = "ON";
        timer = null;
      }else{
        timer = setInterval(()=>{
          Tnumber.value++;
          Snumber.value+=10;
        },1000);
        btnText.value = "OFF";
      }
    }

    return {
      Tjobs,
      Sjobs,
      Tnumber,
      Snumber,
      timer,
      btnText,
      set
    }
  },
  components: {
    myPeople,
  },
};
</script>

