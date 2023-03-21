<template>
  <h1>{{ title }}</h1>
  <!-- <input type="text" ref="name" />
  <button @click="handleClick">Click Me!</button> -->
  <p>Welcome...</p>
  <!-- teleport digunakan untuk element atau komponent ke selector yang dituju ex: class modals yang ada di file index.html -->
  <Teleport to=".modals" v-if="showModal">
    <!-- <Modal :header="header" :text="text" theme="sale" @close="toggleModal" /> -->
    <Modal theme="sale" @close="toggleModal">
      <h1>{{ header }}</h1>
      <p>{{ text }}</p>
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info...</a>
      </template>
    </Modal>
  </Teleport>
  <Teleport to=".modals" v-if="showModalTwo">
    <Modal theme="blue" @close="toggleModalTwo">
      <h1>Modal Two</h1>
      <p>Challenge modal two</p>
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info...</a>
      </template>
    </Modal>
  </Teleport>
  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <button @click="toggleModalTwo" style="margin-left: 0.5rem">
    Open Modal Two
  </button>
</template>

<script>
import Modal from "./components/Modal.vue";
export default {
  name: "App",
  components: {
    Modal,
  },
  data() {
    return {
      title: "My First Vue App :)",
      header: "Sign up for the Giveaway!",
      text: "Grab your ninja swag for half price!",
      showModal: false,
      showModalTwo: false,
    };
  },
  methods: {
    handleClick() {
      console.log(this.$refs.name);
      this.$refs.name.classList.add("active");
      this.$refs.name.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo;
    },
  },
};
</script>

<style>
#app,
.modals {
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
