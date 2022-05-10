<template>
  <div class="about">
    <button @click="open">open</button>
    <div>count {{ count }}</div>
    <AppDialog :is-show="isShow" @close="close">
      <template v-slot:title>title</template>
      <template v-slot:content>
        <button @click="add">+</button>
      </template>
    </AppDialog>
  </div>
</template>

<script>
import AppDialog from "@/components/AppDialog.vue";
import store from "@/store";

export default {
  name: "Demo",
  components: {
    AppDialog,
  },
  data() {
    return {
      isShow: true,
    };
  },
  computed: {
    count() {
      return store.state.count;
    },
  },
  methods: {
    open() {
      this.isShow = true;
    },
    close() {
      this.isShow = false;
    },
    add() {
      store.dispatch("increment");
    },
  },
};
</script>
