<template>
  <button @click="onClick()" :class="[color, 'btn mr-2']">{{ text }}</button>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  methods: {
    onClick() {
this.$emit('toggle-add-task');    },
  },
};
</script>
