<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">
          <button class="btn btnPrimary" @click="modalFirst = true">Show first modal</button>
          <!-- first modal -->
          <modal
          title="First Modal"
          v-if="modalFirst"
          @close="modalFirst = false"></modal>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import modal from '@/components/Modal.vue';

export default {
  name: 'App',
  components: {
    modal,
  },
  data() {
    return {
      modalFirst: false,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
