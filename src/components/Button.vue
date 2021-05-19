<template>
  <div>
    <button
      type="{{type}}"
      @click="onClick()"
      :style="{ 'background-color': bgColor ? bgColor : '#efefef', color: color?  color: 'black'}"
    >
      {{ text }}
    </button>
  </div>
</template>

<script>
export default {
  name: "Button",
  props: {
    text: String,
    type: String,
    color: String,
    bgColor: String
  },
  methods: {
    onClick() {
      this.$emit("button-click");
    },
  },
  emits: ["button-click"],
};
</script>

<style scoped>
button {
  width: 100%;
  height: 30px;
  justify-content: center;
  align-items: center;
  border-radius: 30px;
  min-width: 100px;
  cursor: pointer;
  border: 1px solid grey;
}
</style>
