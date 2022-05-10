<template>
  <div class="dialog-cover" v-if="isShow">
    <div class="dialog">
      <div class="dialog_close" @click="closeDialog">x</div>
      <div class="dialog_title">
        <slot name="title">標題</slot>
      </div>
      <div class="dialog_content">
        <slot name="content">內文</slot>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppDialog",
  props: ["isShow"],
  emits: ["close"],
  methods: {
    closeDialog() {
      this.$emit("close");
    },
  },
};
</script>

<style lang="scss" scoped>
.dialog {
  position: relative;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  color: #2e2c2d;
  font-size: 16px;
  background-color: white;
  width: 300px;
  height: 300px;
}
.dialog_close {
  display: flex;
  justify-content: end;
  font-size: 28px;
  padding-right: 8px;
}
.dialog-cover {
  background: rgba(0, 0, 0, 0.8);
  position: fixed;
  z-index: 999;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
