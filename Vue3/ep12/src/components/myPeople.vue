<template>
  <div>
    <h1>{{ job }}:{{ number }}</h1>
    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    job: String,
    number: Number,
  },
};
</script>

