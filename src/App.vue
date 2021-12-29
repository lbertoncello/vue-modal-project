<template>
  <h1>{{ title }}</h1>
  <p>Welcome...</p>
  <div v-if="showModal">
    <Modal theme="sale" @close="toggleModal">
      <!-- Named slot -->
      <template v-slot:links>
        <a href="#">Sign up now</a>
        <a href="#">More info</a>
      </template>
      <!-- Default slot -->
      <h1>Sign up for the Giveaway!</h1>
      <p>Grab your ninja swag for half price!</p>

    </Modal>
  </div>
  <div v-if="showModalTwo">
    <Modal theme="dark" @close="toggleModalTwo">
      <template v-slot:links>
        <a href="#">Topic 1</a>
        <a href="#">Topic 2</a>
      </template>
      <div>
        <h1>Here you can check out some informations</h1>
        <p>You just need to choose the topic which you want to know more about</p>
      </div>
    </Modal>
  </div>
  <button @click.alt="toggleModal">Open Modal (alt)</button>
  <button @click.shift="toggleModalTwo">Open Modal (shift)</button>
</template>

<script>
import Modal from './components/Modal.vue'

export default {
  name: 'App',
  components: {
    Modal
  },
  data() {
    return {
      title: 'My First Vue App :)',
      showModal: false,
      showModalTwo: false
    }
  },
  methods: {
    toggleModal() {
      this.showModal = !this.showModal
    },
    toggleModalTwo() {
      this.showModalTwo = !this.showModalTwo
    }
  }
}
</script>

<style>
#app {
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
