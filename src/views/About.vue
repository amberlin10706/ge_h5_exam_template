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
  mounted() {
    const timeList = Array(5)
      .fill("")
      .map(() => Math.floor(Math.random() * 6));

    timeList.forEach((time, index) => {
      setTimeout(() => {
        console.log(index + 1);
      }, time * 1000);
    });
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
