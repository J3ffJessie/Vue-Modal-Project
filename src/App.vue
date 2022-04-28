<template>
  <h1>{{ title }}</h1>
  <p>Welcome to our Vue Application</p>
<teleport to=".modals" v-if="showModal">
    <Modal :header="header" :text="text" theme="sale" @close="toggleModal">
        <template v-slot:links>
          <a href="#">Sign Up Now!</a>
          <a href="#">More Info</a>
        </template>  
        <h1>Sign up for the Team!</h1>
        <p>Join the Junior Developer Group!</p>
    </Modal>
</teleport>

<teleport to=".modals" v-if="showModalTwo">
    <Modal :header="header" :text="text" @close="toggleModalTwo"> 
        <h1>Join us on our Discord!</h1>
        <p>Also, follow us on Twitter and Instagram!</p>
    </Modal>
</teleport>
<button @click='toggleModal'>Open Modal</button>
<button @click='toggleModalTwo'>Open Modal Two</button>
</template>




<script>
import Modal from "./components/Modal.vue";

export default {
  name: "App",
  components: { Modal },
  data() {
    return {
      title: "My First Vue Application",
      showModal: false,
      showModalTwo: false
    };
  },
  methods: {
    toggleModal() {
      this.showModal=!this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  },
};
</script>

<style>
#app, .modals {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  border-bottom: 1px solid #ddd;
  display: inline-block;
  padding-bottom: 10px;
}
</style>
