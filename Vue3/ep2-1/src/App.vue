<template>
  <div>
    Year <input type="number" id="text" /> <button @click="check">Get</button>
  </div>
</template>

<script>
export default {
  name: "App",
  setup() {
    let methods = {
      check() {
        let year = document.getElementById("text").value;
        if (
          (year > 0 && year % 400 === 0) ||
          (year % 4 === 0 && year % 100 != 0)
        ) {
          console.log(`${year}是闰年`);
        } else {
          console.log(`${year}不是闰年`);
        }
      },
    };

    return {
      ...methods,
    };
  },
};
</script>

