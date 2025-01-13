<template>
  <div v-show="loaded">
    <NuxtPage />
  </div>
</template>

<script>
export default {
  data() {
    return {
      loaded: false,
    };
  },
  async mounted() {
    // Ожидаем, пока все ресурсы страницы не загрузятся
    await this.waitForLoad();
  },
  methods: {
    waitForLoad() {
      return new Promise((resolve) => {
        if (document.readyState === 'complete') {
          this.loaded = true;
          resolve();
        } else {
          window.addEventListener('load', () => {
            this.loaded = true;
            resolve();
          });
        }
      });
    },
  },
};
</script>
