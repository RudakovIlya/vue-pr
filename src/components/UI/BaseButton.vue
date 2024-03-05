<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: "BaseButton",
};
</script>

<style lang="scss" scoped>
.btn {
  font-family: Verdana, sans-serif;
  display: flex;
  align-items: center;
  cursor: pointer;
  padding: 5px 15px;
  background: #0061d9;
  border-radius: 3px;
  color: #ffffff;
  transition: 0.1s;
  border: none;

  &:hover {
    transition: 0.1s;
    background-color: #013e89;
  }

  &.disabled {
    opacity: 0.5;
  }

  &.disabled:hover {
    background: #0061d9;
  }
}
</style>
