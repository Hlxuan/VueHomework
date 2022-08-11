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

export default {
  name: "App",
  data() {
    return {
      Tjobs: "Teacher",
      Tnumber: 1,
      Sjobs: "Student",
      Snumber: 10,
      btnText: "ON",
      timer: null,
    };
  },
  methods: {
    set() {
      if (this.timer) {
        clearInterval(this.timer);
        this.timer = null;
        this.btnText = "ON";
      } else {
        this.btnText = "OFF";
        this.timer = setInterval(() => {
          this.Tnumber++;
          this.Snumber+=10;
        }, 1000);
      }
    },
  },
  components: {
    myPeople,
  },
};
</script>

<style>
</style>
