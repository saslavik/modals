<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">
          <!-- first modal -->
          <button class="btn btnPrimary" @click="modalFirst = true">Show first modal</button>
          <modal
          title="First Modal"
          v-show="modalFirst"
          @close="modalFirst = false">
          <div slot="body">
            <p>text text text text text </p>
            <button class="btn btnPrimary" @click="modalFirst = false">Well Done</button>
          </div>
          </modal>

          <!-- second modal -->
          <button class="btn btnPrimary" @click="modalSecond.show = true">
            Show modal with form
          </button>
          <modal
          title="Modal with form"
          v-show="modalSecond.show"
          @close="modalSecond.show = false">
          <div slot="body">
            <form @submit.prevent="submitSecondForm">
              <label>Name:</label>
              <input type="text" required v-model="modalSecond.name">
              <label>Email:</label>
              <input type="email" required v-model="modalSecond.email">
              <button class="btn btnPrimary">Submit</button>
            </form>
          </div>
          </modal>

          <button class="btn btnPrimary" @click="modalValidate = true">
            Show modal with form validate
          </button>
          <modalValidate v-show="modalValidate" @close="modalValidate = false"/>
        </div>
      </section>
    </div>
  </div>
</template>

<script>
import modal from '@/components/UI/Modal.vue';
import modalValidate from '@/components/ModalValidate.vue';

export default {
  name: 'App',
  components: {
    modal,
    modalValidate,
  },
  data() {
    return {
      modalFirst: false,
      modalSecond: {
        show: false,
        name: '',
        email: '',
      },
      modalValidate: false,
    };
  },
  methods: {
    submitSecondForm() {
      console.log({
        name: this.modalSecond.name,
        email: this.modalSecond.email,
      });
      this.modalSecond.name = '';
      this.modalSecond.email = '';
      this.modalSecond.show = false;
    },
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
